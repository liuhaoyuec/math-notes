

> [!abstract] 严谨定义
> 设 $X$ 是一个概形。一个 $\mathcal{O}_X$-模层 $\mathcal{L}$ 被称为**可逆层 (Invertible Sheaf)**，如果它在局部上同构于结构层。
> 即存在 $X$ 的一个开覆盖 $\{U_i\}$，使得对于所有的 $i$，都有局部环空间的层同构：
> $$\mathcal{L}|_{U_i} \cong \mathcal{O}_X|_{U_i}$$

## 1. 为什么叫“可逆”？(张量积结构)
在 $\mathcal{O}_X$-模的范畴中，张量积运算 $\otimes_{\mathcal{O}_X}$ 赋予了层一个幺半群结构，其单位元是 $\mathcal{O}_X$。
- $\mathcal{L}$ 是可逆的，当且仅当存在另一个 $\mathcal{O}_X$-模层 $\mathcal{M}$，使得 $\mathcal{L} \otimes_{\mathcal{O}_X} \mathcal{M} \cong \mathcal{O}_X$。
- 这个逆层 $\mathcal{M}$ 实际上就是同态层 $\mathcal{H}om_{\mathcal{O}_X}(\mathcal{L}, \mathcal{O}_X)$，通常记作 $\mathcal{L}^{-1}$ 或 $\mathcal{L}^\vee$（对偶层）。

## 2. 几何对应：线丛 (Line Bundle)
可逆层是微分几何中**复线丛 (Complex Line Bundle)** 在代数几何中的严谨等价物。它的局部秩 (Rank) 处处为 1。

## 3. 终极同构定理
对于任意概形 $X$，存在一个典范的群同构：
$$\text{Pic}(X) \cong H^1(X, \mathcal{O}_X^\times) \cong \{\text{所有可逆层的同构类}\}$$
对于任意 [[卡地亚除子 (Cartier Divisor)]] $D = \{(U_i, f_i)\}$，我们可以严谨构造其关联的可逆层 $\mathcal{O}_X(D)$：在开集 $U \subset U_i$ 上，截面定义为有理函数 $g$ 满足 $g \cdot f_i \in \mathcal{O}_X(U)$。