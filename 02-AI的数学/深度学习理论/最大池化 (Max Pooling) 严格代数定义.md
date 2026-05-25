# 🧠 最大池化 (Max Pooling) 严格代数定义

在最大池化操作中，不存在权重张量 $W$ 与偏置向量 $B$。它是一个确定性的、通道相互正交的非线性降采样算子。

## 1. 拓扑空间与张量定义 (Tensor Spaces)

定义参与运算的张量所在的欧几里得空间：

* **输入张量 (Input)**: $X \in \mathbb{R}^{N \times C \times H_{in} \times W_{in}}$
* **输出张量 (Output)**: $Y \in \mathbb{R}^{N \times C \times H_{out} \times W_{out}}$

*(注：输入通道数与输出通道数恒等，均为 $C$，池化算子在深度切片上是绝对正交且独立的。)*

## 2. 负无穷延拓张量 (Negative-Infinity Padded Tensor)

由于最大池化使用的是上确界算子（$\max$），为防止边缘零填充（Zero-Padding）对负数特征值产生干扰，必须定义基于 $-\infty$ 的延拓张量 $\tilde{X}$。
令空间填充参数为 $(p_H, p_W)$，则 $\tilde{X} \in (\mathbb{R} \cup \{-\infty\})^{N \times C \times (H_{in} + 2p_H) \times (W_{in} + 2p_W)}$ 的分段映射为：

$$
\tilde{X}[n, c, h, w] = 
\begin{cases} 
X[n, c, h - p_H, w - p_W], & \text{if } p_H \le h < H_{in} + p_H \text{ and } p_W \le w < W_{in} + p_W \\ 
-\infty, & \text{otherwise} 
\end{cases}
$$

## 3. 核心代数方程 (The Rigorous Equation)

在给定池化核大小 $(k_H, k_W)$、步长 $(s_H, s_W)$ 以及空洞膨胀系数 $(d_H, d_W)$ 的严格约束下，输出张量 $Y$ 中任意标量元素的绝对方程为：

$$
Y[n, c, y, x] = \max_{i=0}^{k_H-1} \max_{j=0}^{k_W-1} \Big( \tilde{X}[n, c, \, y \cdot s_H + i \cdot d_H, \, x \cdot s_W + j \cdot d_W] \Big)
$$

**【算子解析】**
* **独立性**: 左侧坐标 $c$ 直接映射右侧切片 $c$，无 $\sum$ 求和，证明各通道数据不发生任何张量收缩或融合。
* **极值提取**: $\max$ 算子在被仿射映射（$y \cdot s_H + i \cdot d_H$）约束的二维离散子集内，提取上确界。

## 4. 离散边界映射定理 (Dimension Mapping)

输出特征图的拓扑维度 $(H_{out}, W_{out})$ 的离散缩减规律，与卷积算子保持绝对一致：

$$
H_{out} = \left\lfloor \frac{H_{in} + 2p_H - d_H \cdot (k_H - 1) - 1}{s_H} \right\rfloor + 1
$$
$$
W_{out} = \left\lfloor \frac{W_{in} + 2p_W - d_W \cdot (k_W - 1) - 1}{s_W} \right\rfloor + 1
$$