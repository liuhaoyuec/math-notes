# 拟凝聚层 (Quasi-coherent Sheaf)

> [!abstract] 严谨定义 (基于局部表现)
> 一个 $\mathcal{O}_X$-模层 $\mathcal{F}$ 是**拟凝聚的 (Quasi-coherent)**，如果 $X$ 可以被开集覆盖 $\{U_i\}$，使得在每一个 $U_i$ 上，$\mathcal{F}$ 存在一个**精确的正合序列 (Exact Sequence)** 形式的自由模表现：
> $$\mathcal{O}_{U_i}^{(J)} \to \mathcal{O}_{U_i}^{(I)} \to \mathcal{F}|_{U_i} \to 0$$
> 其中 $I$ 和 $J$ 是任意基数的指标集。
> *(白话解释：$\mathcal{F}$ 局部上完全可以由一组（可能无限多）生成元和一组（可能无限多）线性关系来严格定义。)*

## 1. 仿射概形上的等价刻画 (至关重要)
Grothendieck 的核心定理：设 $X = \text{Spec}(A)$ 是一个仿射概形。
函子 $M \mapsto \tilde{M}$ 给出了从 **$A$-模范畴** 到 **$X$ 上的拟凝聚层范畴** 的**范畴等价**。
- $\tilde{M}$ 的构造：对于任意主开集 $D(f)$，定义 $\tilde{M}(D(f)) = M_f = M \otimes_A A_f$（即对模进行局部化）。
- **结论**：拟凝聚层就是把经典的交换代数模论，完美、无损地“涂抹”到了整个概形的拓扑空间上。

## 2. 几何意义
拟凝聚性排除了那些“不随着拓扑变化而进行合理局部化”的病态阿贝尔群层。所有的理想层 (Ideal Sheaves)、结构层 $\mathcal{O}_X$ 本身、以及相对微分层 $\Omega^1_{X/Y}$ 都是拟凝聚层。

**进阶链接**：添加有限性条件即得到 [[凝聚层 (Coherent Sheaf)]]。