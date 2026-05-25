# 交换环范畴 (CRing Category)

> [!abstract] 严谨定义
> **交换环范畴**，记作 $\mathbf{CRing}$，是 $\mathbf{Ring}$ 的全子范畴。
> - **对象 (Objects)**：所有的交换含幺环 (Commutative Unital Rings)。
> - **态射 (Morphisms)**：保单位元的环同态。

## 核心性质与代数几何的基石
$\mathbf{CRing}$ 是代数几何最直接的代数镜像。
- **余乘积 (Coproduct)**：在 $\mathbf{CRing}$ 中，两个交换环 $A$ 和 $B$ 的余乘积是它们在 $\mathbb{Z}$ 上的**张量积 (Tensor Product)** $A \otimes_{\mathbb{Z}} B$。（这与群范畴中的自由积完全不同）。
- **反变等价 (Contravariant Equivalence)**：根据 Grothendieck 的理论，$\mathbf{CRing}$ 范畴与 [[仿射概形 (Affine Scheme)]] 范畴是**绝对反变等价**的。函子 $\text{Spec}(-)$ 将交换环的态射完全反向转化为仿射概形之间的拓扑连续与局部环映射。