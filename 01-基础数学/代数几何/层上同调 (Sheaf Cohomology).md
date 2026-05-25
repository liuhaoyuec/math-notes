# 层上同调 (Sheaf Cohomology)

> [!abstract] 严谨定义
> 设 $X$ 是一个拓扑空间（例如概形）。设 $\mathbf{Ab}(X)$ 或 $\mathbf{Mod}(X)$ 为 $X$ 上的阿贝尔层或 $\mathcal{O}_X$-模层构成的范畴。
> $X$ 上的**全局截面函子 (Global Section Functor)** $\Gamma(X, -)$ 是一个左正合函子。
> 某一层 $\mathcal{F}$ 的**第 $i$ 阶层上同调群 $H^i(X, \mathcal{F})$**，被极其严谨地定义为全局截面函子的第 $i$ 个右导函子：
> $$ H^i(X, \mathcal{F}) := R^i \Gamma(X, \mathcal{F}) $$

## 1. 为什么需要层上同调？(局部到整体的障碍)
层论的核心性质是“局部可粘合”。如果有一个开覆盖 $\{U_i\}$，并且在每个 $U_i$ 上有截面 $s_i$，只要它们在交集上相容，就能唯一拼成全局截面。
- **层正合序列的断裂**：对于层的短正合序列 $0 \to \mathcal{F} \to \mathcal{G} \to \mathcal{H} \to 0$，取全局截面后，我们只得到左正合序列：
  $$ 0 \to \Gamma(X, \mathcal{F}) \to \Gamma(X, \mathcal{G}) \to \Gamma(X, \mathcal{H}) $$
  **最后的满射性丢失了！** 这意味着：$\mathcal{H}$ 的一个全局截面，在局部上虽然都能被 $\mathcal{G}$ 覆盖，但这些局部原像**拼不起来**。
- **上同调的介入**：$H^1(X, \mathcal{F})$ 正是测量这个“拼不起来”的障碍群。如果 $H^1(X, \mathcal{F}) = 0$，则满射性成立。

## 2. 几何与代数特性
- **第 0 阶**：$H^0(X, \mathcal{F}) = \Gamma(X, \mathcal{F})$，即极其直观的全局截面本身。
- **高阶**：$H^i(X, \mathcal{F})$ 对于所有的内射层均为 0。高阶上同调纯粹是由空间的拓扑结构（如洞的个数、覆盖的复杂性）和层本身的扭曲程度共同激发的代数实体。