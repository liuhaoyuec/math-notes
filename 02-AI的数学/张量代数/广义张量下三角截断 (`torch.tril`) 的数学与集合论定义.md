# 🧮 广义张量下三角截断 (`torch.tril`) 的数学与集合论定义

> [!info] 核心法则：最后两维法则 (The Last-Two-Dimensions Rule)
> 对于任意维度 $n \ge 2$ 的张量，`torch.tril` 及其对角线偏移量 `diagonal`，永远只作用于张量的**最后两个索引**（即“行”和“列”），而对其余的前 $n-2$ 个索引实行无差别的**广播（Broadcast）遍历**。

---

## 1. 变量与集合定义

设输入张量为 $X$，其维度大小为一个 $n$ 元组：$(D_0, D_1, \dots, D_{n-2}, D_{n-1})$。
设偏移参数为 $k \in \mathbb{Z}$（即代码中的 `diagonal=k`）。

我们定义张量 $X$ 中的任意一个元素为：
$$x_{i_0, i_1, \dots, i_{n-2}, i_{n-1}}$$

在这个索引序列中，我们赋予最后两个索引特殊的物理意义：
* **行索引 (Row Index)**：$r = i_{n-2}$
* **列索引 (Column Index)**：$c = i_{n-1}$

前 $n-2$ 个索引 $(i_0, \dots, i_{n-3})$ 构成了**批次坐标空间 $\mathcal{B}$**。

## 2. 集合论视角的掩码条件

我们定义一个**保留集合 (Keep Set) $\mathcal{K}$**，它包含了所有不需要被清零的元素的索引坐标。
对于坐标 $(i_0, \dots, r, c)$，它属于保留集合 $\mathcal{K}$ 的充分必要条件是：**列索引不得超过行索引加上偏移量 $k$**。

用严格的集合符号表示为：
$$\mathcal{K} = \left\{ (i_0, \dots, r, c) \mid c \le r + k \right\}$$

*(推论：当 $k=0$ 时，条件退化为 $c \le r$，这正是标准下三角矩阵的代数定义。)*

## 3. 映射函数 (Piecewise Mapping)

设输出张量为 $Y = \text{torch.tril}(X, \text{diagonal}=k)$。
则 $Y$ 中的每一个元素 $y_{i_0, \dots, r, c}$ 由以下分段函数严格映射：

$$y_{i_0, \dots, i_{n-2}, i_{n-1}} = \begin{cases} x_{i_0, \dots, i_{n-2}, i_{n-1}}, & \text{如果 } (i_0, \dots, i_{n-2}, i_{n-1}) \in \mathcal{K} \\ 0, & \text{如果 } (i_0, \dots, i_{n-2}, i_{n-1}) \notin \mathcal{K} \end{cases}$$

等价的纯索引不等式表达：
$$Y[\dots, r, c] = \begin{cases} X[\dots, r, c], & \text{if } c - r \le k \\ 0, & \text{if } c - r > k \end{cases}$$

> [!check] 结论
> 无论你的张量前面叠加了多少维（比如 `[Batch, Heads, Seq_len, Seq_len]` 这个 4 维注意力矩阵），`tril` 都会像一台拥有无数个分身的切割机，进入每一个 Batch 和 Head 中，对着最后的那个 `[Seq_len, Seq_len]` 的二维矩阵，精准地切下同样的一刀。