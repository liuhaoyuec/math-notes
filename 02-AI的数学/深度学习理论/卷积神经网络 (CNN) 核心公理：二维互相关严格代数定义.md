# 🧠 卷积神经网络 (CNN) 核心公理：二维互相关严格代数定义

> [!abstract] 核心本质
> 深度学习中的 `Conv2d` 在严格数学定义上为**二维互相关 (2D Cross-Correlation)**。它本质上是从高维坐标空间 $\Omega$ 到实数域 $\mathbb{R}$ 的仿射映射与多维黎曼和的坍缩。

---

## 1. 拓扑空间与张量定义 (Tensor Spaces)
定义参与运算的四个张量所在的欧几里得空间：

* **输入张量 (Input)**: $X \in \mathbb{R}^{N \times C_{in} \times H_{in} \times W_{in}}$
* **权重张量 (Kernel)**: $W \in \mathbb{R}^{C_{out} \times C_{in} \times k_H \times k_W}$
* **偏置向量 (Bias)**: $B \in \mathbb{R}^{C_{out}}$
* **输出张量 (Output)**: $Y \in \mathbb{R}^{N \times C_{out} \times H_{out} \times W_{out}}$

*(注：$N$ 为 Batch Size，$C$ 为 Channel，$k$ 为 Kernel Size)*

---

## 2. 边界延拓张量 (Zero-Padded Tensor)
为防止感受野滑动时下标越界，必须定义基于零填充的延拓张量 $\tilde{X}$。
令空间填充参数为 $(p_H, p_W)$，则 $\tilde{X} \in \mathbb{R}^{N \times C_{in} \times (H_{in} + 2p_H) \times (W_{in} + 2p_W)}$ 定义为：

$$
\tilde{X}[n, c, h, w] = 
\begin{cases} 
X[n, c, h - p_H, w - p_W], & \text{if } p_H \le h < H_{in} + p_H \text{ and } p_W \le w < W_{in} + p_W \\ 
0, & \text{otherwise} 
\end{cases}
$$

---

## 3. 核心代数方程 (The Rigorous Equation)
在给定步长 $(s_H, s_W)$ 和空洞膨胀系数 $(d_H, d_W)$ 的约束下，输出张量 $Y$ 的绝对微观标量方程为：

$$
Y[n, c_{out}, y, x] = B[c_{out}] + \sum_{c_{in}=0}^{C_{in}-1} \sum_{i=0}^{k_H-1} \sum_{j=0}^{k_W-1} W[c_{out}, c_{in}, i, j] \cdot \tilde{X}[n, c_{in}, y \cdot s_H + i \cdot d_H, x \cdot s_W + j \cdot d_W]
$$

**【下标约束解析】**
* **坐标锁定**: $n$ (图片), $c_{out}$ (卷积核), $(y, x)$ (输出空间系)。
* **三重内积**: $\sum_{c_{in}}$ 确保深度融合，$\sum_{i} \sum_{j}$ 执行 $k_H \times k_W$ 感受野内的点积。
* **仿射映射**: $y \cdot s_H$ 为原点平移（步长调制），$+ i \cdot d_H$ 为核内采样偏移（膨胀系数调制）。

---

## 4. 离散边界定理 (Dimension Output Mapping)
输出特征图的拓扑维度 $(H_{out}, W_{out})$ 必须严格服从以下下取整离散方程：

$$
H_{out} = \left\lfloor \frac{H_{in} + 2p_H - d_H \cdot (k_H - 1) - 1}{s_H} \right\rfloor + 1
$$
$$
W_{out} = \left\lfloor \frac{W_{in} + 2p_W - d_W \cdot (k_W - 1) - 1}{s_W} \right\rfloor + 1
$$

---

## 5. 💡 进阶视角：集合论与泛函映射
> [!info] 张量的函数本质
> 张量 $X$ 并非单纯的“多维数组”，而是定义在离散坐标空间 $\Omega = \mathcal{N} \times \mathcal{C} \times \mathcal{H} \times \mathcal{W}$ 上的映射函数。
> 即 $X \in \{ f \mid f: \Omega \rightarrow \mathbb{R} \}$。
> 表达式 $X[n, c, h, w]$ 实则为求值操作 $X(\omega) = v$，而底层的 C++ 是通过字典序映射算子 (Lexicographical Stride Mapping) 将四维坐标 $\omega$ 强制双射至一维物理内存地址。