# 相对微分层 (Relative Differential Sheaf)

> [!abstract] 严谨定义 (层化构造)
> 设 $f: X \to Y$ 是一个概形态射。
> 概形 $X$ 上的**相对微分层 $\Omega^1_{X/Y}$** 是通过将局部的 [[凯勒微分模 (Module of Kähler Differentials)]] 在整个拓扑空间上进行层化 (Sheafification) 而严密构造出的 $\mathcal{O}_X$-模层。

## 1. 仿射局部构造与粘合
- 对于 $X$ 和 $Y$ 上的任意一对适配仿射开集 $U = \text{Spec}(B) \subset X$ 和 $V = \text{Spec}(A) \subset Y$（满足 $f(U) \subset V$），定义层 $\Omega^1_{X/Y}$ 在 $U$ 上的截面为 $\Omega_{B/A}$ 对应的拟凝聚层。
- 由于凯勒微分的构造与局部化严格交换（即 $\Omega_{S^{-1}B/A} \cong S^{-1}\Omega_{B/A}$），这些局部层能够完美地粘合为一个整体的 [[拟凝聚层 (Quasi-coherent Sheaf)]] $\Omega^1_{X/Y}$。

## 2. 几何对应与平滑性判定
- **余切丛的代数化身**：当 $Y = \text{Spec}(k)$ 且 $X$ 为 $k$ 上的平滑代数簇时，$\Omega^1_{X/k}$ 严格对应于微分几何中的**余切丛 (Cotangent Bundle)**。
- **平滑性的代数判定**：若 $X \to Y$ 是有限型态射，则该态射是 [[平滑与正则态射 (Smooth and Regular Morphism)]]，**当且仅当** $\Omega^1_{X/Y}$ 是一个**局部自由层 (Locally Free Sheaf)**（即秩在连通分支上恒定的向量丛），且其秩精确等于态射的相对维数。

**进阶链接**：对平滑代数簇取其最高阶外代数，即得到 [[规范层 (Canonical Sheaf)]]。