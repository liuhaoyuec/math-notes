# 同调代数：$\text{Tor}$ 函子 (Tor Functor)

> [!abstract] 范畴论本质：极限破缺的度量
> - **张量积 $-\otimes_R B$ 是左伴随函子**，因此它天生只保余极限（右正合），**必定会破坏极限（单射/核）**。
> - **$\text{Tor}_n^R(-, B)$ 是张量积的左导出函子 (Left Derived Functor)**。
> - **终极物理意义：** $\text{Tor}$ 函子精确测量了张量积在试图保持单射（极限）时，所产生的“误差”或“失败程度”。如果 $\text{Tor}_1 = 0$，则单射被完美保留。

---

## 1. 严格代数构造：投射分解的流水线

计算 $\text{Tor}_n^R(A, B)$ 需要执行一套极其严格的四步代数流水线：

> [!info] 步骤 1：投射分解 (Projective Resolution)
> 为模 $A$ 寻找一个由完美的投射模（如自由模）$P_i$ 组成的正合序列。这是对 $A$ 的内部结构进行“无损展开”。
> 
> $$ \dots \xrightarrow{d_3} P_2 \xrightarrow{d_2} P_1 \xrightarrow{d_1} P_0 \xrightarrow{\epsilon} A \to 0 $$

> [!info] 步骤 2：截断/斩首 (Truncation)
> 砍掉末尾的目标模 $A$ 以及 $\to 0$，得到一个在 $P_0$ 处不再正合的复形 $P_\bullet$。
> 
> $$ \dots \xrightarrow{d_3} P_2 \xrightarrow{d_2} P_1 \xrightarrow{d_1} P_0 \to 0 $$

> [!info] 步骤 3：施加张量积 (Tensor Product)
> 将截断后的复形 $P_\bullet$ 的每一项与 $B$ 作张量积，得到新的链复形 $P_\bullet \otimes_R B$。
> 
> $$ \dots \xrightarrow{d_3 \otimes 1} P_2 \otimes_R B \xrightarrow{d_2 \otimes 1} P_1 \otimes_R B \xrightarrow{d_1 \otimes 1} P_0 \otimes_R B \to 0 $$

> [!info] 步骤 4：求同调 (Homology)
> 新复形在第 $n$ 个位置（即 $P_n \otimes_R B$ 处）的同调群，就是 $\text{Tor}_n$：
> 
> $$ \text{Tor}_n^R(A, B) := \frac{\ker(d_n \otimes 1)}{\text{im}(d_{n+1} \otimes 1)} $$
> 
> *(注：当 $n=0$ 时，$\text{Tor}_0^R(A, B) \cong A \otimes_R B$，即原本的张量积自身。)*

---

## 2. 核心代数定理

> [!check] 定理 1：双函子与平衡定理 (Balancing Theorem)
> $\text{Tor}_n^R(A, B)$ 对 $A$ 和 $B$ 是绝对对称的。
> 你既可以用 $A$ 的投射分解去张量 $B$，也可以用 $B$ 的投射分解去张量 $A$，求出的同调群**自然同构**。

> [!check] 定理 2：长正合序列 (Long Exact Sequence) —— “打捞”定理
> 给定任意短正合序列 $0 \to M_1 \xrightarrow{f} M_2 \xrightarrow{g} M_3 \to 0$。
> 施加张量积 $-\otimes_R N$ 后，单射 $f \otimes 1$ 可能被破坏。系统强制诱导出一个长正合序列来修补：
> 
> $$ \dots \to \text{Tor}_1(M_3, N) \xrightarrow{\delta} M_1 \otimes N \xrightarrow{f \otimes 1} M_2 \otimes N \xrightarrow{g \otimes 1} M_3 \otimes N \to 0 $$
> 
> **逻辑印证：** 因为正合，所以 $\text{im}(\delta) = \ker(f \otimes 1)$。单射被破坏产生的异常核，由 $\text{Tor}_1$ 严丝合缝地填补。

> [!check] 定理 3：平坦模 (Flat Module)
> 如果一个模 $F$ 与任何模做张量积都**绝不破坏单射**（即 $-\otimes F$ 是绝对正合函子），则称 $F$ 为**平坦模**。
> **等价定义：** 对于所有 $n \ge 1$ 且所有模 $M$，都有 $\text{Tor}_n^R(M, F) = 0$。
> *(注：自由模和投射模绝对是平坦模，这也是为什么 $\mathbb{Z}$ 系数下算不出 $\text{Tor}$ 的根本原因。)*

---

## 3. 在代数拓扑中的终极降临：单纯同调 UCT

在拓扑学中，我们将链群复形的系数从 $\mathbb{Z}$ 转换为任意环 $G$。这本质上是施加了 $-\otimes_\mathbb{Z} G$ 函子。由于张量积的破缺，必须引入 $\text{Tor}$ 函子进行修正。

> [!abstract] 同调万有系数定理 (Universal Coefficient Theorem for Homology)
> $$ H_k(X; G) \cong (H_k(X; \mathbb{Z}) \otimes G) \oplus \text{Tor}_1^\mathbb{Z}(H_{k-1}(X; \mathbb{Z}), G) $$
> 
> **公式拆解：**
> 1. **直接观测部分 ($H_k \otimes G$)：** 原本 $k$ 维空间的自由孔洞，在 $G$ 系数下的直接映射。
> 2. **升维异常部分 ($\text{Tor}_1$)：** 第 $k-1$ 维中存在的**挠 (Torsion)** 结构，在张量积代数摩擦下发生极限破缺，被 $\text{Tor}_1$ 捕捉，并强行在第 $k$ 维制造出一个新的同调类。