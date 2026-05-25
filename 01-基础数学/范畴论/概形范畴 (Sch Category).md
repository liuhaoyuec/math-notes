# 概形范畴 (Sch Category)

> [!abstract] 严谨定义
> **概形范畴**，记作 $\mathbf{Sch}$。
> - **对象 (Objects)**：所有的 [[概形 (Scheme)]]（局部同构于仿射概形的局部环空间）。
> - **态射 (Morphisms)**：局部环空间的态射（拓扑连续映射 + 保局部环极大理想的结构层同态）。

## 核心性质
- **终对象 (Terminal Object)**：$\text{Spec}(\mathbb{Z})$。任何一个概形都有且仅有一个态射映射到 $\text{Spec}(\mathbb{Z})$。（这说明整数环是所有代数几何的绝对基底，算术几何由此诞生）。
- **极限的存在性**：$\mathbf{Sch}$ 拥有所有的有限极限，其中最核心的就是 [[纤维积 (Fiber Product)]] $X \times_S Y$。
- **反变等价**：它的全子范畴 **仿射概形范畴** $\mathbf{AffSch}$ 与 [[交换环范畴 (CRing Category)]] 严格反变等价（箭头全部反转）。