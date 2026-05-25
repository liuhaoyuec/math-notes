# 🧠 CNN 训练范式：数学流形优化与工程映射

> [!abstract] 核心本质
> 神经网络的训练，在数学上是寻找泛函空间中经验风险极小值点（Empirical Risk Minimization）的非凸优化过程；在工程上是依托有向无环计算图（DAG）进行的自动微分（Autograd）与张量更新。

*(注：本文默认已掌握前置公理 `[二维互相关定义]`、`[离散边界映射定理]` 与 `[特征张量演化漏斗]`，不再复述空间维度的降采样过程。)*

---

## 1. 前向传播与经验风险 (Forward Pass & Empirical Risk)

**【数学定义】**
整个 CNN 是一个巨大的参数化复合映射 $F(X; \Theta)$，其中 $\Theta = \{W_1, B_1, W_2, B_2, \dots \}$ 为全网权重张量集。
给定批次输入 $X \in \mathbb{R}^{N \times C \times H \times W}$ 与真实标签向量 $Y$，网络输出预测概率 $\hat{Y} = F(X; \Theta)$。

为了衡量当前特征流形的误差，定义**交叉熵损失函数 (Cross-Entropy Loss)** $\mathcal{L}$，它度量了预测分布与真实分布的 KL 散度：
$$
\mathcal{L}(\Theta) = - \frac{1}{N} \sum_{i=1}^{N} \sum_{c=1}^{Classes} Y_{i,c} \log(\hat{Y}_{i,c})
$$

**【工程映射】**
在 PyTorch 中，前向传播隐式构建了计算图，并保存了计算梯度的必要中间张量（Context Tensors）。
```python
# [工程代码] 前向拓扑计算与标量坍缩
outputs = model(inputs)            # 复合函数求值: \hat{Y} = F(X; \Theta)
loss = criterion(outputs, labels)  # 计算标量流形误差: \mathcal{L}(\Theta)
```

---

## 2. 反向传播与链式法则 (Backpropagation)

**【数学定义】**
训练的唯一目标是求取损失标量 $\mathcal{L}$ 对每一个权重张量 $W_l$ 的雅可比矩阵（Jacobian）/ 梯度向量 $\nabla_{W_l} \mathcal{L}$。
依据多元微积分的**链式法则 (Chain Rule)**，梯度从计算图末端逐层回传：
$$
\frac{\partial \mathcal{L}}{\partial W_l} = \frac{\partial \mathcal{L}}{\partial Y_L} \cdot \frac{\partial Y_L}{\partial Y_{L-1}} \cdots \frac{\partial Y_{l+1}}{\partial Y_l} \cdot \frac{\partial Y_l}{\partial W_l}
$$
*定理：由于卷积在底层同构于托普利茨矩阵的全连接乘法，上述所有偏导均可严格转化为高维张量的收缩运算。*

**【工程映射】**
`loss.backward()` 是整个深度学习引擎的灵魂。它逆序遍历 DAG 计算图，调用底层 CUDA 内核求解导数，并将结果硬编码写入每个参数对象的 `.grad` 属性中。
```python
# [工程代码] 梯度流反向穿透计算图
optimizer.zero_grad()  # 清空驻留梯度 (强制梯度正交化，防累加)
loss.backward()        # 触发自动微分引擎，计算所有 \nabla_{W} \mathcal{L}
```

---

## 3. 参数空间更新 (Parameter Space Update)

**【数学定义】**
获取梯度后，在参数空间中执行流形下降。以带有动量（Momentum）和权重衰减（L2 正则化）的随机梯度下降（SGD）为例：
定义速度向量 $V_l$，学习率 $\eta$，正则化系数 $\lambda$。
离散时间步 $t \to t+1$ 的更新算子为：
$$
V_l^{(t+1)} = \mu V_l^{(t)} + \nabla_{W_l} \mathcal{L} + \lambda W_l^{(t)}
$$
$$
W_l^{(t+1)} = W_l^{(t)} - \eta V_l^{(t+1)}
$$

**【工程映射】**
优化器直接越过计算图，对物理内存中的权重张量执行 in-place（原地）代数更新。
```python
# [工程代码] 步进流形极小值
optimizer.step()  # 执行张量代数更新：W = W - \eta * \nabla W
```

---

## 4. 💡 核心架构级 PyTorch 严谨实现

以下代码严格遵循 `Conv -> Conv -> Learnable Downsample (步长卷积)` 的现代骨干网络架构公理。

```python
import torch
import torch.nn as nn
import torch.optim as optim

class RigorousCNN(nn.Module):
    def __init__(self, num_classes=10):
        super(RigorousCNN, self).__init__()
        
        # 1. 特征流形提取区 (Feature Extraction)
        # 遵循连续小核卷积定理，扩大感受野并增加非线性流形复杂度
        self.features = nn.Sequential(
            # Layer 1: 映射到高维正交特征空间
            nn.Conv2d(in_channels=3, out_channels=64, kernel_size=3, padding=1, bias=False),
            nn.BatchNorm2d(64),
            nn.ReLU(inplace=True),
            
            # Layer 2: 同维特征组合
            nn.Conv2d(in_channels=64, out_channels=64, kernel_size=3, padding=1, bias=False),
            nn.BatchNorm2d(64),
            nn.ReLU(inplace=True),
            
            # Layer 3: 可学习空间降维 (替代 MaxPool，交由反向传播自适应优化)
            # 物理跨度 J 翻倍，空间维度 (H, W) 坍缩 50%
            nn.Conv2d(in_channels=64, out_channels=128, kernel_size=3, stride=2, padding=1, bias=False),
            nn.BatchNorm2d(128),
            nn.ReLU(inplace=True)
        )
        
        # 2. 空间坍缩算子 (Global Average Pooling)
        # 将 R^{N x C x H x W} 暴力积分为 R^{N x C x 1 x 1}
        self.adaptive_pool = nn.AdaptiveAvgPool2d((1, 1))
        
        # 3. 语义分类算子 (Classifier)
        # 将基底特征线性组合为高级类别语义
        self.classifier = nn.Linear(in_features=128, out_features=num_classes)

    def forward(self, x):
        x = self.features(x)                # [N, 128, H/2, W/2]
        x = self.adaptive_pool(x)           # [N, 128, 1, 1]
        x = torch.flatten(x, 1)             # [N, 128] 解除空间维度拓扑
        out = self.classifier(x)            # [N, num_classes]
        return out

# --- 绝对严谨的训练流形映射 ---
def train_epoch(model, dataloader, device):
    model.train()  # 激活 Dropout/BatchNorm 的动态统计特性
    
    # 定义度量空间与下降算子
    criterion = nn.CrossEntropyLoss()
    optimizer = optim.SGD(model.parameters(), lr=0.01, momentum=0.9, weight_decay=1e-4)
    
    for batch_idx, (inputs, labels) in enumerate(dataloader):
        inputs, labels = inputs.to(device), labels.to(device)
        
        # 1. 经验风险前向评估
        outputs = model(inputs)
        loss = criterion(outputs, labels)
        
        # 2. 计算图梯度求导
        optimizer.zero_grad() 
        loss.backward()       
        
        # 3. 权重流形步进
        optimizer.step()      
        
        if batch_idx % 100 == 0:
            print(f"流形标量误差 (Loss): {loss.item():.6f}")
```