# 🧠 张量维度操作的绝对代数法则 (Softmax vs 归约)

> [!info] 核心思想：“铁签子”穿刺法则
> 在 N 维张量中指定 `dim=m`，等价于：**死死固定其他 $N-1$ 个维度的坐标（自由指标），派出探测器 $k$（哑指标）专门沿着第 $m$ 个维度从头遍历到底。**

---

## 1. 结构保留操作：Softmax
**【物理动作】** 签子穿进去，把上面的数字按比例缩放成概率，然后原样退出。
**【维度变化】** 形状绝对不变（输入 $N$ 维 $\rightarrow$ 输出 $N$ 维）。

**数学索引公式：**
$$
Y[i_1]\dots[j]\dots[i_n] = \frac{e^{X[i_1]\dots[j]\dots[i_n]}}{\sum_{k=1}^{S_m} e^{X[i_1]\dots[k]\dots[i_n]}}
$$
*(注：等式两边的中括号数量严格相等，维度完美保留)*

**PyTorch 实战代码：**
```python
import torch
X = torch.randn(32, 12, 100) # [Batch, Heads, Seq_Len]

# 沿着最后一个维度算概率 (大模型 Attention 标准写法)
Y = torch.softmax(X, dim=-1) 
# Y.shape 依然是 [32, 12, 100]
```

---

## 2. 维度坍缩操作：归约家族 (Reduction)
**【物理动作】** 签子穿进去，把整根签子上的所有数字暴力捏碎，变成 1 个单一的数字。
**【维度变化】** 第 $m$ 维在物理空间被抹除（输入 $N$ 维 $\rightarrow$ 输出 $N-1$ 维）。

**核心数学索引公式：**
注意看等号左边的 $Y$，代表第 $m$ 维的中括号**直接消失了**！
$$
Y[i_1]\dots[i_{m-1}][i_{m+1}]\dots[i_n] = \mathbf{Op}_{k=1}^{S_m} \Big( X[i_1]\dots[k]\dots[i_n] \Big)
$$

具体函数只是把操作符 $\mathbf{Op}$ 换掉：
* **求和 (Sum):** $\sum_{k=1}^{S_m} X[\dots]$
* **均值 (Mean):** $\frac{1}{S_m} \sum_{k=1}^{S_m} X[\dots]$
* **最大值 (Max):** $\max_{k \in \{1 \dots S_m\}} X[\dots]$
* **连乘 (Prod):** $\prod_{k=1}^{S_m} X[\dots]$

**PyTorch 实战代码：**
```python
X = torch.randn(32, 12, 100)

# 求和：捏碎第 1 维 (长度为12)
sum_out = torch.sum(X, dim=1)  # shape 变成 [32, 100]

# 求均值：捏碎最后一维
mean_out = torch.mean(X, dim=-1) # shape 变成 [32, 12]

# 求最大值：注意 max 会返回两个张量 (最大值本身 和 所在的索引位置)
max_val, max_idx = torch.max(X, dim=1) 
```

---

## 3. 工程救命稻草：`keepdim=True`
> [!warning] 避坑铁律：防止广播机制报错
> 归约操作导致维度减少后，如果拿去和原张量做加减法，必定报错。必须用 `keepdim=True` 强行留住该维度的“尸体”。

**数学意义：** 把该维度保留，强制令其长度等于 1。
$$
Y[i_1]\dots[\mathbf{1}]\dots[i_n] = \sum_{k} X[i_1]\dots[k]\dots[i_n]
$$

**PyTorch 实战代码：**
```python
X = torch.randn(32, 100)

# 错误做法：导致形状无法相减
# Y = torch.sum(X, dim=1)         # shape: [32]
# X_centered = X - Y              # ❌ 崩溃！[32, 100] 无法减去 [32]

# 正确做法：留住空壳
Y_kept = torch.sum(X, dim=1, keepdim=True) # shape: [32, 1]
X_centered = X - Y_kept           # ✅ 完美广播计算！[32,100] - [32,1]
```