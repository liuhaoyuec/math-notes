# 概形 (Scheme)

> [!abstract] 严谨定义
> 一个**概形**是一个局部环空间 $(X, \mathcal{O}_X)$，使得 $X$ 能够被一组开集 $\{U_i\}_{i \in I}$ 覆盖，并且对每一个 $i$，赋环空间 $(U_i, \mathcal{O}_X|_{U_i})$ 作为局部环空间同构于某个 [[仿射概形 (Affine Scheme)]] $\text{Spec}(A_i)$。

## 1. 前置知识与组件
- **局部环空间 (Locally Ringed Space)**：一个拓扑空间 $X$ 配备一个交换环层 $\mathcal{O}_X$，且对于任意一点 $x \in X$，其茎 (Stalk) $\mathcal{O}_{X,x}$ 都是一个局部环（即有唯一的极大理想）。
- **仿射概形 (Affine Scheme)**：形式为 $\text{Spec}(A)$ 的局部环空间，其点集为交换环 $A$ 的所有素理想，拓扑为 Zariski 拓扑，结构层由局部化环 $A_\mathfrak{p}$ 定义。

## 2. 态射的定义
设 $(X, \mathcal{O}_X)$ 和 $(Y, \mathcal{O}_Y)$ 为概形。一个**概形态射 (Morphism of Schemes)** $f: X \to Y$ 是局部环空间的态射。
它由两部分组成：
1. 连续映射 $f: X \to Y$。
2. 层同态 $f^\#: \mathcal{O}_Y \to f_* \mathcal{O}_X$。
**附加极其严苛的条件**：对于任意 $x \in X$，$f^\#$ 在茎上诱导的环同态 $f^\#_x: \mathcal{O}_{Y, f(x)} \to \mathcal{O}_{X, x}$ 必须是**局部环同态**（即把源局部环的极大理想映射到目标局部环的极大理想内部）。

## 3. 几何直觉与意义
概形是代数几何中“空间”的终极泛化。它允许空间携带无穷小结构（通过包含幂零元），并统一了数论（如 $\text{Spec}(\mathbb{Z})$）和几何（如 $\mathbb{C}$ 上的代数簇）。所有的 [[古典代数簇 (Classical Algebraic Variety)]] 都可以通过完全忠实函子等价地视为特定类型的概形。