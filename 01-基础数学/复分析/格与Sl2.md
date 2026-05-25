# 格的基底与模群 $SL_2(\mathbb{Z})$ 的双射关系

> [!warning] 概念辨析：基底变换 vs 自同构
> - **基底变换**：格 $\Lambda$ 保持不动，改变的是生成该格的两个基向量 $(\omega_1, \omega_2)$。$SL_2(\mathbb{Z})$ 描述的正是这种变换。
> - **格的自同构**：指的是存在复数 $\alpha \in \mathbb{C}$，使得 $\alpha\Lambda = \Lambda$。对于绝大多数格，自同构群只有 $\{\pm 1\}$。

## 1. 核心定义

### 1.1 复平面上的格 (Lattice)
在复平面 $\mathbb{C}$ 中，给定两个在实数域 $\mathbb{R}$ 上线性无关的复数 $\omega_1, \omega_2$。由它们的所有整数线性组合构成的离散子群称为**格** $\Lambda$：
$$\Lambda = \mathbb{Z}\omega_1 \oplus \mathbb{Z}\omega_2 = \{ m\omega_1 + n\omega_2 \mid m, n \in \mathbb{Z} \}$$
有序对 $(\omega_1, \omega_2)$ 称为该格的一个**基底**。

### 1.2 正定向基底 (Oriented Basis)
为了统一几何方向并与上半平面 $\mathbb{H}$ 建立联系，我们要求基底向量的排列顺序满足逆时针方向。
若基底 $(\omega_1, \omega_2)$ 满足：
$$\text{Im}\left(\frac{\omega_1}{\omega_2}\right) > 0$$
则称 $(\omega_1, \omega_2)$ 为格 $\Lambda$ 的一个**正定向基底**。
令 **$\mathcal{B}(\Lambda)$** 表示格 $\Lambda$ 的**所有正定向基底构成的集合**。

### 1.3 模群 (Modular Group) $SL_2(\mathbb{Z})$
特殊线性群 $SL_2(\mathbb{Z})$ 定义为所有元素为整数、且行列式为 1 的 $2 \times 2$ 矩阵构成的乘法群：
$$SL_2(\mathbb{Z}) = \left\{ \begin{pmatrix} a & b \\ c & d \end{pmatrix} \mathrel{\Bigg|} a,b,c,d \in \mathbb{Z}, \ ad - bc = 1 \right\}$$

---

## 2. 双射定理与证明

**定理**：给定一个固定的格 $\Lambda$。若选定其任意一个正定向基底 $B_0 = \begin{pmatrix} \omega_1 \\ \omega_2 \end{pmatrix} \in \mathcal{B}(\Lambda)$ 作为参考基准，那么模群 $SL_2(\mathbb{Z})$ 与该格的正定向基底集合 $\mathcal{B}(\Lambda)$ 之间存在一一对应关系（双射）。

即，映射 $\Phi : SL_2(\mathbb{Z}) \to \mathcal{B}(\Lambda)$ 如下定义是一个双射：
$$\Phi(\gamma) = \gamma B_0 = \begin{pmatrix} a & b \\ c & d \end{pmatrix} \begin{pmatrix} \omega_1 \\ \omega_2 \end{pmatrix} = \begin{pmatrix} a\omega_1 + b\omega_2 \\ c\omega_1 + d\omega_2 \end{pmatrix}$$

### 证明过程

欲证 $\Phi$ 是双射，需证明其既是单射（Injective），又是满射（Surjective）。

#### 第一步：证明满射 (Surjectivity)
**目标**：对于集合 $\mathcal{B}(\Lambda)$ 中的任意一个正定向基底 $B' = \begin{pmatrix} \omega_1' \\ \omega_2' \end{pmatrix}$，都能在 $SL_2(\mathbb{Z})$ 中找到一个矩阵 $\gamma$，使得 $B' = \gamma B_0$。

1. **存在整数矩阵**：因为 $B_0$ 和 $B'$ 都是同一个格 $\Lambda$ 的基底，所以 $B'$ 中的元素必然能由 $B_0$ 整数线性表出，反之亦然。因此存在整数矩阵 $M, N \in M_2(\mathbb{Z})$ 使得 $B' = M B_0$ 且 $B_0 = N B'$。
2. **行列式为 $\pm 1$**：代入可得 $B_0 = NM B_0$。因为 $\omega_1, \omega_2$ 线性无关，所以 $NM = I$。由于 $N, M$ 均为整数矩阵，这要求 $\det(M)\det(N) = 1$，且它们都是整数，故 $\det(M) = \pm 1$。
3. **定向条件限定行列式为 1**：由于 $B_0$ 和 $B'$ 都是正定向的，即 $\text{Im}(\omega_1/\omega_2) > 0$ 且 $\text{Im}(\omega_1'/\omega_2') > 0$。根据虚部变换公式：
   $$\text{Im}\left(\frac{\omega_1'}{\omega_2'}\right) = \frac{\det(M)}{|c(\omega_1/\omega_2) + d|^2} \text{Im}\left(\frac{\omega_1}{\omega_2}\right)$$
   要保证等式两边符号同为正，必须要求 $\det(M) > 0$。
4. **结论**：结合 2 和 3，$\det(M) = 1$。因此 $M \in SL_2(\mathbb{Z})$。令 $\gamma = M$，满射得证。

#### 第二步：证明单射 (Injectivity)
**目标**：如果 $\gamma_1 B_0 = \gamma_2 B_0$，那么必定有 $\gamma_1 = \gamma_2$。

1. 设 $\gamma_1 = \begin{pmatrix} a_1 & b_1 \\ c_1 & d_1 \end{pmatrix}$，$\gamma_2 = \begin{pmatrix} a_2 & b_2 \\ c_2 & d_2 \end{pmatrix}$。
2. 已知条件可写为 $(\gamma_1 - \gamma_2) B_0 = 0$，展开即：
   $$\begin{cases} (a_1 - a_2)\omega_1 + (b_1 - b_2)\omega_2 = 0 \\ (c_1 - c_2)\omega_1 + (d_1 - d_2)\omega_2 = 0 \end{cases}$$
3. 由于 $B_0 = (\omega_1, \omega_2)$ 是格的基底，它们在 $\mathbb{R}$ 上是线性无关的（自然在 $\mathbb{Z}$ 上也线性无关）。
4. 线性无关意味着上述等式成立的唯一条件是系数全为零，即 $a_1 = a_2, b_1 = b_2, c_1 = c_2, d_1 = d_2$。
5. 因此 $\gamma_1 = \gamma_2$，单射得证。

**总结**：由于映射 $\Phi$ 既是单射又是满射，所以它是一个双射。这就说明了，在固定一个初始正定向基底后，**格的所有可能的正定向基底，与 $SL_2(\mathbb{Z})$ 中的矩阵一一对应**。

---
