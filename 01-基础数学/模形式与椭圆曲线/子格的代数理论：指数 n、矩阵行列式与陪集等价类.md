# 子格的代数理论：指数 $n$、矩阵行列式与陪集等价类

> [!abstract] 核心主旨
> 本笔记旨在严格证明关于格 $\Lambda$ 的子格 $\Lambda'$ 的两个核心等价性：
> 1. **群论与行列式的等价**：子群的指数 $[\Lambda : \Lambda'] = n$ 严格等价于其基底过渡矩阵的行列式绝对值为 $n$。
> 2. **子格计数与商集的等价**：寻找所有不同的指数为 $n$ 的子格，严格等价于寻找矩阵集合对于 $\text{SL}_2(\mathbb{Z})$ 的左陪集（即商去等价类）。

---

## 核心定理 1：商群的阶 = 矩阵的行列式

**定理表述：** 设 $\Lambda = \mathbb{Z}\omega_1 \oplus \mathbb{Z}\omega_2$ 是复平面上的格。设 $\Lambda'$ 是 $\Lambda$ 的子格，其基底由整数矩阵 $M \in M_2(\mathbb{Z})$ 给出，即 $\begin{pmatrix} \omega'_1 \\ \omega'_2 \end{pmatrix} = M \begin{pmatrix} \omega_1 \\ \omega_2 \end{pmatrix}$。
则商群 $\Lambda / \Lambda'$ 的阶（即子格的指数）等于矩阵 $M$ 的行列式的绝对值：
$$[\Lambda : \Lambda'] = |\Lambda / \Lambda'| = |\det(M)|$$

> [!quote] 证明：基于史密斯标准型 (Smith Normal Form)
> 因为 $\Lambda$ 是一个秩为 2 的自由阿贝尔群，同构于 $\mathbb{Z}^2$。我们可以把 $\Lambda$ 中的元素看作 $\mathbb{Z}^2$ 中的列向量坐标。
> 在这个坐标系下，原格 $\Lambda \cong \mathbb{Z}^2$，而子格 $\Lambda'$ 对应的坐标集合就是 $M^T \mathbb{Z}^2$ （因为基底是左乘，坐标就是右乘或转置左乘，为书写方便我们研究 $M \mathbb{Z}^2$，其行列式与 $M^T$ 相同）。
> 
> 根据**整数矩阵的史密斯标准型定理**，对于任意一个非奇异的 $2 \times 2$ 整数矩阵 $M$，必定存在两个可逆的整数矩阵 $P, Q \in \text{GL}_2(\mathbb{Z})$（即 $\det(P)=\pm 1, \det(Q)=\pm 1$），使得：
> $$P M Q = D = \begin{pmatrix} d_1 & 0 \\ 0 & d_2 \end{pmatrix}$$
> 其中 $d_1, d_2$ 是正整数，且 $d_1 \mid d_2$（$d_1$ 整除 $d_2$）。
> 
> 我们来计算商群 $\mathbb{Z}^2 / M\mathbb{Z}^2$ 的结构。
> 因为 $P$ 和 $Q$ 都是 $\mathbb{Z}^2$ 到自身的群同构映射（双射），在群同构的意义下，左乘 $P$ 或右乘 $Q$ 不改变商群的势（元素的个数）：
> $$\mathbb{Z}^2 / M\mathbb{Z}^2 \cong \mathbb{Z}^2 / (P M Q) \mathbb{Z}^2 = \mathbb{Z}^2 / D\mathbb{Z}^2$$
> 
> 对角矩阵 $D\mathbb{Z}^2$ 的作用极其明显，它就是把第一个坐标轴的单位长拉伸了 $d_1$ 倍，第二个拉伸了 $d_2$ 倍：
> $$D\mathbb{Z}^2 = (d_1 \mathbb{Z}) \oplus (d_2 \mathbb{Z})$$
> 
> 因此，商群可以直接直和分解：
> $$\mathbb{Z}^2 / D\mathbb{Z}^2 \cong (\mathbb{Z} / d_1\mathbb{Z}) \oplus (\mathbb{Z} / d_2\mathbb{Z})$$
> 
> 这个商群的元素个数（即阶数）显然是这两个循环群阶数的乘积：
> $$|\Lambda / \Lambda'| = d_1 \cdot d_2$$
> 
> 另一方面，我们对史密斯标准型等式 $P M Q = D$ 两边同时取行列式：
> $$\det(P) \cdot \det(M) \cdot \det(Q) = \det(D) = d_1 \cdot d_2$$
> 因为 $\det(P) = \pm 1, \det(Q) = \pm 1$，取绝对值即得：
> $$|\det(M)| = d_1 \cdot d_2$$
> 
> **结论：** $|\Lambda / \Lambda'| = |\det(M)|$。如果规定保定向（$M$ 的行列式为正），则商群的阶就是 $\det(M)$。$\blacksquare$

---

## 核心定理 2：寻找不同子格 = 商去 $\text{SL}_2(\mathbb{Z})$ 的等价类

**定理表述：** 给定格 $\Lambda$，寻找所有**纯几何意义上不同**的、且保定向的指数为 $n$ 的子格 $\Lambda'$。这在代数上等价于寻找矩阵集合 $\mathcal{M}_n = \{ M \in M_2(\mathbb{Z}) \mid \det(M) = n \}$ 对群 $\text{SL}_2(\mathbb{Z})$ 的**左陪集（Left Cosets）**。

> [!danger] 核心迷思：矩阵不同 $\neq$ 子格不同
> 一个行列式为 $n$ 的矩阵 $M \in \mathcal{M}_n$ 可以帮我们算出一组新基底，从而生成一个指数为 $n$ 的子格 $\Lambda'$。
> 但是！如果我随便拿另一个行列式为 $n$ 的矩阵，它可能生成的是**同一个**子格（只是用了该子格里另一组不同的基底而已）。
> 为了不重复计数，我们必须“商去等价类”。

> [!quote] 证明：等价类与左陪集的精准对应
> 设有两个矩阵 $M_1, M_2 \in \mathcal{M}_n$，它们分别作用于原基底 $E = \begin{pmatrix} \omega_1 \\ \omega_2 \end{pmatrix}$，生成了两组新基底：
> $$E_1 = M_1 E, \quad E_2 = M_2 E$$
> 这两组新基底生成的子格分别记为 $\Lambda'_1$ 和 $\Lambda'_2$。
> 
> **问：在什么条件下，这两个子格在几何上完全重合（即 $\Lambda'_1 = \Lambda'_2$）？**
> 根据我们在“一般格自同构”中严格证明过的结论：两个基底生成同一个格的充要条件是，它们之间可以通过一个全模群矩阵相互转化。因为我们要求保定向，所以这个转换矩阵必须是 $\gamma \in \text{SL}_2(\mathbb{Z})$。
> 
> 也就是说，存在 $\gamma \in \text{SL}_2(\mathbb{Z})$，使得：
> $$E_1 = \gamma E_2$$
> 将 $M$ 的表达式代入：
> $$M_1 E = \gamma (M_2 E) = (\gamma M_2) E$$
> 因为原基底 $E$ 是线性无关的，所以必须有：
> $$M_1 = \gamma M_2$$
> 
> **逻辑收网：**
> 在代数中，如果两个元素满足 $M_1 = \gamma M_2$（其中 $\gamma$ 属于某个群 $G$），我们就说这两个元素属于**同一个左陪集（Left Coset）**。
> 
> 因此，任意一个**唯一的确定的子格**，并不对应一个孤立的矩阵，而是对应着一整个等价类：
> $$[M] = \{ \gamma M \mid \gamma \in \text{SL}_2(\mathbb{Z}) \}$$
> 这个等价类就是左陪集 $\text{SL}_2(\mathbb{Z}) M$。
> 
> **结论：** 寻找所有互不相同的指数为 $n$ 的子格，在代数上就是寻找商集（等价类空间）中的元素：
> $$\text{SL}_2(\mathbb{Z}) \backslash \mathcal{M}_n$$
> *(注：在 Hecke 算子理论中，我们通常选取埃尔米特标准型 (Hermite Normal Form) $\begin{pmatrix} a & b \\ 0 & d \end{pmatrix}$ 且 $ad=n, 0 \le b < d$ 作为这些左陪集的完美代表元集合。)* $\blacksquare$