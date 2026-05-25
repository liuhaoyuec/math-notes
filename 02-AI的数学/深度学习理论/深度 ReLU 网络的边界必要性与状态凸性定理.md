# 深度 ReLU 网络的边界必要性与状态凸性定理

## 1. 核心定义与命题陈述

> [!info] 前置定义 (Definitions)
> 设 $F: \mathbb{R}^{n_0} \to \mathbb{R}^d$ 为一个包含仿射变换和 ReLU 激活的深度神经网络。
> 设 $\Omega_A$ 和 $\Omega_B$ 为输入空间中两个不同的**独立解析线性区域**。由于区域不同，它们对应的端到端雅可比矩阵必然不同，即已知条件为：**$\mathbf{C}_A \neq \mathbf{C}_B$**。
> 
> 设 $S(\mathbf{x}) \in \{0, 1\}^{N_{neurons}}$ 为输入点 $\mathbf{x}$ 在整个网络中触发的神经元激活状态组合（状态码）。
> 设 $\mathcal{S}_A = \{S(\mathbf{x}) \mid \mathbf{x} \in \Omega_A\}$ 为区域 $\Omega_A$ 包含的所有可能状态码的集合。
> 设 $\mathcal{S}_B = \{S(\mathbf{x}) \mid \mathbf{x} \in \Omega_B\}$ 为区域 $\Omega_B$ 包含的所有可能状态码的集合。

在此基础上，我们提出两个描述网络边界跨越的命题：

> [!abstract] 命题陈述 (Propositions)
> **命题 P (代数状态视角)：** 两个不同解析区域所包含的神经元状态集合，其交集必定为空，即 **$\mathcal{S}_A \cap \mathcal{S}_B = \emptyset$**。
> 
> **命题 Q (拓扑几何视角)：** 对于任意一条从 $\Omega_A$ 内部走向 $\Omega_B$ 内部的连续路径 $\gamma$，都必定存在至少一个隐藏层神经元，使得它的预激活值 $z$ 在这条路径上发生了跨越 $0$ 的变号（即必定跨越至少一个超平面边界）。

---

## 2. 命题等价性证明 ($P \iff Q$)

这两个命题看似视角不同，但在 ReLU 的几何性质下是完全等价的绝对真理。

> [!example] 证明 1：正向推导 ($P \implies Q$)
> **思路：基于离散状态映射的连续性。**
> 1. 已知 $\mathcal{S}_A \cap \mathcal{S}_B = \emptyset$。
> 2. 考虑任意连续路径 $\gamma(t)$，起点状态 $S_{start} \in \mathcal{S}_A$，终点状态 $S_{end} \in \mathcal{S}_B$。
> 3. 因为交集为空，所以 $S_{start} \neq S_{end}$。
> 4. 在这条连续路径上，离散的状态码 $S(\gamma(t))$ 无法一直保持不变，必定在某处发生了改变。
> 5. 状态码改变的物理等价条件，就是至少有一个二进制位发生翻转，即至少有一个神经元的输入 $z$ 跨越了 $0$。命题 $Q$ 成立。 $\blacksquare$

> [!example] 证明 2：反向推导 ($Q \implies P$)
> **思路：利用逆否命题（$\neg P \implies \neg Q$）与 ReLU 状态空间的凸性（Convexity）。**
> 6. 假设 $\mathcal{S}_A \cap \mathcal{S}_B \neq \emptyset$，即存在一个共同的状态码 $S_{overlap}$。
> 7. 在 $\Omega_A$ 中选取一点 $\mathbf{x}_A$ 满足 $S(\mathbf{x}_A) = S_{overlap}$；在 $\Omega_B$ 中选取一点 $\mathbf{x}_B$ 满足 $S(\mathbf{x}_B) = S_{overlap}$。
> 8. **凸性引理：** 任何一个固定的状态码 $S$，等价于要求所有神经元的激活条件（$\mathbf{w}_i^T \mathbf{x} + b_i > 0$ 或 $\le 0$）同时满足。这是无数个半空间的交集，其在输入空间中构成的几何体必定是一个**凸多面体（Convex Polytope）**。
> 9. 根据凸性定义，连接 $\mathbf{x}_A$ 和 $\mathbf{x}_B$ 的**直线段**上的所有点，必然也都位于这个凸多面体内部。
> 10. 这意味着，我们构造出了一条从 $\Omega_A$ 到 $\Omega_B$ 的直线路径，且该路径上的所有点都共享完全相同的状态码 $S_{overlap}$。
> 11. 既然状态码未发生任何翻转，这条路径就**没有跨越任何神经元的 $0$ 边界**。这推翻了命题 $Q$。逆否命题得证，故 $Q \implies P$ 成立。 $\blacksquare$

---

## 3. 命题真实性证明

我们已经证明了 $P$ 和 $Q$ 是一回事。现在用最简明的代数逻辑证明命题 $P$ 本身是绝对正确的。

> [!check] 绝对真理证明 (Proof of Proposition P)
> 1. 根据神经网络的链式法则，端到端雅可比矩阵 $\mathbf{C}$ 由当前的网络状态码 $S$ 和固定的权重矩阵 $\mathbf{W}$ 唯一确定。这是一个确定的单值映射函数：$\mathbf{C} = \text{Func}(S)$。
> 2. 我们使用反证法。假设 $\mathcal{S}_A \cap \mathcal{S}_B \neq \emptyset$。
> 3. 这意味着存在一个重叠状态码 $S_{overlap}$，它既属于 $\Omega_A$，又属于 $\Omega_B$。
> 4. 既然它属于 $\Omega_A$，则 $\text{Func}(S_{overlap}) = \mathbf{C}_A$。
> 5. 既然它属于 $\Omega_B$，则 $\text{Func}(S_{overlap}) = \mathbf{C}_B$。
> 6. 由此必然推导出：**$\mathbf{C}_A = \mathbf{C}_B$**。
> 7. 这与我们的前提条件（两个区域解析不同，即 $\mathbf{C}_A \neq \mathbf{C}_B$）发生了绝对的数学矛盾！
> 8. 因此，反证法假设不成立。原命题 $\mathcal{S}_A \cap \mathcal{S}_B = \emptyset$ 绝对成立。 $\blacksquare$