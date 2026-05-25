# 卡地亚除子 (Cartier Divisor)

> [!abstract] 严谨定义 (代数除子)
> 设 $X$ 是任意概形。令 $\mathcal{K}_X$ 为 $X$ 上的**全商环层 (Sheaf of total quotient rings)**，$\mathcal{K}_X^\times$ 为其可逆元层，$\mathcal{O}_X^\times$ 为结构层的可逆元层。
> $X$ 上的一个**卡地亚除子 (Cartier Divisor)** 是商层 $\mathcal{K}_X^\times / \mathcal{O}_X^\times$ 的一个**全局截面 (Global Section)**。

## 1. 局部显式刻画 (核心操作)
全局截面在局部上表现为一组数据 $\{(U_i, f_i)\}$，满足：
1. $\{U_i\}$ 是 $X$ 的一个开覆盖。
2. $f_i \in \mathcal{K}_X^\times(U_i)$（即 $f_i$ 是 $U_i$ 上的非零有理函数）。
3. **转移条件 (相容性)**：在交集 $U_i \cap U_j$ 上，商 $f_i / f_j \in \mathcal{O}_X^\times(U_i \cap U_j)$（即它们的商是一个没有极点也没有零点的严格可逆正则函数）。

## 2. 卡地亚与韦伊的等价性
- **从卡地亚到韦伊**：如果 $X$ 满足 [[韦伊除子 (Weil Divisor)]] 的所有前提条件，任何卡地亚除子 $\{(U_i, f_i)\}$ 都可以唯一对应到一个韦伊除子：在 $U_i$ 上取 $\text{div}(f_i)$ 并粘合。
- **极其重要的定理**：如果 $X$ 进一步是**局部阶乘的 (Locally Factorial)**（例如所有平滑簇/正则概形），则**卡地亚除子群与韦伊除子群严格自然同构**。

## 3. 皮卡群 (Picard Group)
- **主卡地亚除子**：如果存在一个全局有理函数 $f \in \mathcal{K}_X^\times(X)$，使得所有 $f_i = f$，则称其为主除子。
- 两个卡地亚除子之差为主除子时称它们**线性等价**。其等价类构成的群称为 $X$ 的**皮卡群 $\text{Pic}(X)$**。

**进阶链接**：卡地亚除子天然对应于 [[可逆层 (Invertible Sheaf)]]。