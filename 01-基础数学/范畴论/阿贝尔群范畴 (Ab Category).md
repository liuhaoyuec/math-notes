# 阿贝尔群范畴 (Ab Category)

> [!abstract] 严谨定义
> **阿贝尔群范畴**，记作 $\mathbf{Ab}$，是 $\mathbf{Grp}$ 的全子范畴 (Full Subcategory)。
> - **对象 (Objects)**：所有的交换群 (Abelian Groups)。
> - **态射 (Morphisms)**：群同态。

## 核心性质与阿贝尔范畴的基石
$\mathbf{Ab}$ 是代数几何和同调代数中最核心的范畴，它是**阿贝尔范畴 (Abelian Category)** 的原型。
- **加法结构**：对于任意对象 $A, B$，态射集 $\text{Hom}_{\mathbf{Ab}}(A, B)$ 本身天然构成一个阿贝尔群（通过 $(f+g)(x) = f(x)+g(x)$）。复合运算对加法是双线性的。
- **有限双积 (Biproduct)**：在 $\mathbf{Ab}$ 中，有限乘积（直积 $A \times B$）和有限余乘积（直和 $A \oplus B$）是**绝对同构**的。这与 $\mathbf{Grp}$ 形成了极其鲜明的对比。
- 它允许严密定义核 (Kernel) 和上核 (Cokernel)，从而可以展开所有同调代数的运算（正合序列、导函子等）。