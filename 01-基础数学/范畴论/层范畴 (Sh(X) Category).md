# 层范畴 (Sh(X) Category)

> [!abstract] 严谨定义
> 设 $X$ 为一个拓扑空间，$\mathcal{C}$ 为某个底范畴（通常是 $\mathbf{Set}$ 或 $\mathbf{Ab}$）。**$X$ 上的 $\mathcal{C}$-值层范畴**记作 $\mathbf{Sh}(X, \mathcal{C})$。
> - **对象 (Objects)**：满足局部恒等和粘合公理的层 $\mathcal{F}$。
> - **态射 (Morphisms)**：层同态 (Morphisms of Sheaves)，即一族与限制映射相容的自然变换。



## 核心性质 (以阿贝尔层为例)
当 $\mathcal{C} = \mathbf{Ab}$ 时，$\mathbf{Sh}(X, \mathbf{Ab})$ 是一个**阿贝尔范畴**。
- **极其反直觉的满射性**：层同态 $f: \mathcal{F} \to \mathcal{G}$ 是“满态射”，并不意味着每一个截面映射 $\mathcal{F}(U) \to \mathcal{G}(U)$ 都是满射！它只要求在**茎 (Stalks)** 层面上是满射（即局部上总是存在原像）。
- 这种截面满射性的缺失，直接催生了用右导函子来测量的 [[层上同调 (Sheaf Cohomology)]]。