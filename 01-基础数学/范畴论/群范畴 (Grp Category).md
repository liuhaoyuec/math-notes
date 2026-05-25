# 群范畴 (Grp Category)

> [!abstract] 严谨定义
> **群范畴**，记作 $\mathbf{Grp}$。
> - **对象 (Objects)**：所有的群 (Groups)。
> - **态射 (Morphisms)**：群同态 (Group Homomorphisms)，即保持群乘法操作的映射 $f(xy) = f(x)f(y)$。

## 核心性质
- **零对象 (Zero Object)**：平凡群 $\{e\}$。它同时是始对象和终对象。
- **乘积 (Product)**：群的直积 $G \times H$。
- **余乘积 (Coproduct)**：群的自由积 (Free Product) $G * H$（注意：不是直和！非交换群的余乘积非常庞大且复杂）。
- **态射的单满性**：在 $\mathbf{Grp}$ 中，单态射 (Monomorphism) 严格等价于单射，满态射 (Epimorphism) 严格等价于满射。

**进阶链接**：其交换子范畴为 [[阿贝尔群范畴 (Ab Category)]]。