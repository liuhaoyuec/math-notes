# 古典代数簇 (Classical Algebraic Variety)

> [!abstract] 根本定义 (基于 Serre 的 FAC 体系)
> 设 $k$ 为代数闭域。一个 $k$ 上的**古典代数簇**是一个配备了 $k$-代数层的拓扑空间 $(X, \mathcal{O}_X)$，且严格满足以下两个公理：
> 1. **局部仿射性 (Locally Affine)**：存在 $X$ 的一个有限开覆盖 $\{U_i\}$，使得每一个带有诱导层结构的局部环空间 $(U_i, \mathcal{O}_X|_{U_i})$ 都作为局部环空间同构于某个 [[仿射簇 (Affine Variety)]]。
> 2. **分离性 (Separatedness)**：对角线态射 $\Delta: X \to X \times X$（定义为 $x \mapsto (x, x)$）的像在乘积拓扑 $X \times X$ 中是一个**闭集**。

## 核心注记
- $\mathcal{O}_X$ 是 $X$ 上的**正则函数层**（其截面是取值于 $k$ 的连续函数，且局部上可以用多项式之商表示）。
- **分离性**的代数几何本质等价于拓扑学中的 Hausdorff 条件。如果丢掉分离性公理，会得到病态的“带两个原点的直线”（仿射直线在除了原点之外的所有地方自粘合）。
- 所有的 [[拟射影簇 (Quasi-Projective Variety)]]（自然也包括 [[射影簇 (Projective Variety)]]）都严格满足这个定义。