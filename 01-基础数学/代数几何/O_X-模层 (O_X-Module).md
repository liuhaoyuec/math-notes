# O_X-模层 (O_X-Module)

> [!abstract] 严谨定义
> 设 $(X, \mathcal{O}_X)$ 为一个赋环空间（例如概形）。$X$ 上的一个 **$\mathcal{O}_X$-模层** $\mathcal{F}$ 是一个阿贝尔群层，并且对于任意开集 $U$，$\mathcal{F}(U)$ 被赋予了一个 $\mathcal{O}_X(U)$-模的结构。
> 这种模结构必须与限制映射相容：对于任意 $V \subset U$ 和 $a \in \mathcal{O}_X(U), s \in \mathcal{F}(U)$，满足 $\rho_{UV}(a \cdot s) = \rho_{UV}(a) \cdot \rho_{UV}(s)$。

## 1. 核心意义
在交换代数中，我们研究环 $A$ 上的 $M$-模。在代数几何中，由于空间是被 $\mathcal{O}_X$ 局部粘合的，所以线性代数也必须被局部化并粘合。$\mathcal{O}_X$-模层就是**代数几何中执行线性代数运算的基底对象**。

## 2. 基础操作
所有的层论操作都可以在 $\mathcal{O}_X$-模层上进行：
- **直和**：$\mathcal{F} \oplus \mathcal{G}$
- **张量积**：$\mathcal{F} \otimes_{\mathcal{O}_X} \mathcal{G}$（由局部张量积生成的层化）。
- **层同态**：$\mathcal{H}om_{\mathcal{O}_X}(\mathcal{F}, \mathcal{G})$。

但普通的 $\mathcal{O}_X$-模层过于宽泛（可能与底空间的几何毫无关系），必须对其施加极其严格的代数限制，即将其收敛为 [[拟凝聚层 (Quasi-coherent Sheaf)]]。