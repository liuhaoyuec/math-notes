# PyTorch 实战核心：5层全连接网络拟合正弦曲线

## 核心代码片段 (The Code)
这是深度学习最标准的训练模板，无论是拟合简单曲线还是训练千亿大模型，都逃不开这套骨架。

```python
import torch

# 1. 准备数据 (Data)
# linspace生成一维张量，unsqueeze强插维度变成 [100, 1]，以满足 Linear 层对末尾维度的严格要求
X_coor = torch.unsqueeze(torch.linspace(-5, 5, 100), dim=1)
# 纯粹的逐元素操作 (Element-wise)，生成真实标签
Y_rea = torch.sin(X_coor)

# 2. 搭建模型 (Model)
# Sequential 是串行容器。Linear(输入维, 输出维) 执行 X @ W^T + b
model = torch.nn.Sequential(
    torch.nn.Linear(1, 16),
    torch.nn.ReLU(),       # 打破线性死板，如果没有 ReLU，多层 Linear 会坍缩为一层
    torch.nn.Linear(16, 16),
    torch.nn.ReLU(),
    torch.nn.Linear(16, 1) # 最终压缩回1维标量输出
)

# 3. 裁判与执行者 (Loss & Optimizer)
loss_func = torch.nn.MSELoss()
# 核心解耦：将 model 内部所有 W 和 b 的内存指针，打包交给 Adam 优化器
optimizer = torch.optim.Adam(model.parameters(), lr=0.001)

# 4. 训练循环 (Training Loop)
for epoch in range(0, 100):
    # ① 正向算值：传入特征，构建计算图，拿到预测结果
    pred = model(X_coor)
    
    # ② 评判误差：生成带有反向指针 (grad_fn) 的标量特洛伊木马
    loss = loss_func(pred, Y_rea)
    
    # ③ 清空旧账：【铁律】执行反向传播前，必须清空优化器掌控的所有 .grad 抽屉
    optimizer.zero_grad()
    
    # ④ 反向传播：点燃引信，C++引擎顺着计算图指针回溯，计算每个参数的偏导并塞入 .grad
    loss.backward()
    
    # ⑤ 统一迈步：优化器读取算好的 .grad，执行 W = W - lr * grad 的参数更新
    optimizer.step()