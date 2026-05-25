# 层化与包含伴随对 (Sheafification ⊣ Inclusion)

> [!abstract] 严谨定义
> 设 $X$ 是一个拓扑空间。令 $\mathbf{PSh}(X)$ 为 $X$ 上的预层 (Presheaf) 范畴，$\mathbf{Sh}(X)$ 为 [[层范畴 (Sh(X) Category)]]。
> 存在一对伴随函子：
> - **右伴随函子 (遗忘/包含)**：包含函子 $i: \mathbf{Sh}(X) \to \mathbf{PSh}(X)$。它纯粹地把一个层看作预层，遗忘其粘合公理。
> - **左伴随函子 (自由构造)**：层化函子 (Associated Sheaf Functor) $a: \mathbf{PSh}(X) \to \mathbf{Sh}(X)$（也常记作 $\mathcal{F}^+$）。
> 
> **伴随同构**：对于任意预层 $\mathcal{F}$ 和层 $\mathcal{G}$，存在自然双射：
> $$\text{Hom}_{\mathbf{Sh}(X)}(a(\mathcal{F}), \mathcal{G}) \cong \text{Hom}_{\mathbf{PSh}(X)}(\mathcal{F}, i(\mathcal{G}))$$

## 1. 层化的泛性质
上述伴随关系严格等价于层化的泛性质：任何从预层 $\mathcal{F}$ 到一个严格层 $\mathcal{G}$ 的预层同态，都**存在且唯一**地分解为 $\mathcal{F} \to a(\mathcal{F}) \to \mathcal{G}$。层化 $a(\mathcal{F})$ 是最逼近原预层的层。

## 2. 为什么层的操作如此反直觉？(极限与余极限的不对称性)
- **右伴随 $i$ 保持极限**：这解释了为什么两个层态射的**核 (Kernel)**、层的**直积 (Direct Product)** 在预层层面计算完毕后，**它天生就已经是一个层了！** 完全不需要层化。
- **左伴随 $a$ 保持余极限**：这解释了为什么两个层态射的**上核 (Cokernel)**、层的**张量积 (Tensor Product)**、以及层的**直和 (Direct Sum)**，如果在预层层面直接计算，得到的结果通常**绝对不是层**。必须在预层计算完毕后，**强制施加一次左伴随 $a$ (层化)**，才能得到真正的层级余极限。