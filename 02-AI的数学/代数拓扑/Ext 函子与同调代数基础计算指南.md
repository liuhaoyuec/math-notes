# Ext 函子与同调代数基础计算指南

> [!abstract] 核心思想
> $\text{Ext}_R^n(M, N)$ 是一个双函子，用于衡量模范畴中正合性被破坏的程度。它的核心优势在于**平衡定理 (Balancing Theorem)**：既可以通过对 $M$ 进行投射分解来计算，也可以通过对 $N$ 进行内射分解来计算，两者的结果是典范同构的。

---

## 1. 基础分解 (Resolutions)

在计算 Ext 群之前，我们需要对变元进行“柔化”处理，即寻找它们在投射模或内射模构成的链复形中的体现。

> [!definition] 投射分解 (Projective Resolution)
> 对于 $R$-模 $M$，其投射分解是一个**正合列 (Exact Sequence)**，其中所有的 $P_i$ 均为投射模：
> $$ \cdots \xrightarrow{d_{n+1}} P_n \xrightarrow{d_n} P_{n-1} \xrightarrow{d_{n-1}} \cdots \xrightarrow{d_2} P_1 \xrightarrow{d_1} P_0 \xrightarrow{\epsilon} M \to 0 $$
> **正合性要求：** 
> * $\text{im}(d_{n+1}) = \ker(d_n)$
> * $\text{im}(d_1) = \ker(\epsilon)$
> * $\epsilon$ 为满射。

> [!definition] 内射分解 (Injective Resolution)
> 对于 $R$-模 $N$，其内射分解是一个**正合列 (Exact Sequence)**，其中所有的 $I^i$ 均为内射模：
> $$ 0 \to N \xrightarrow{\eta} I^0 \xrightarrow{d^0} I^1 \xrightarrow{d^1} I^2 \xrightarrow{d^2} \cdots $$
> **正合性要求：**
> * $\text{im}(\eta) = \ker(d^0)$
> * $\text{im}(d^n) = \ker(d^{n+1})$
> * $\eta$ 为单射。

---

## 2. Ext 函子的两种计算体系

### 途径 A：分解左变元 $M$ (投射分解法)

这是最常用的计算方式，利用 $\text{Hom}_R(-, N)$ 的逆变性。

**步骤 1：截断复形**
去掉投射分解正合列中的目标模 $M$，得到一个链复形 $P_\bullet$（此时在 $P_0$ 处不再正合）：
$$ \cdots \xrightarrow{d_3} P_2 \xrightarrow{d_2} P_1 \xrightarrow{d_1} P_0 \to 0 $$

**步骤 2：施加 Hom 函子**
对上述复形施加逆变函子 $\text{Hom}_R(-, N)$，所有箭头方向反转，得到余链复形：
$$ 0 \to \text{Hom}_R(P_0, N) \xrightarrow{d_1^*} \text{Hom}_R(P_1, N) \xrightarrow{d_2^*} \text{Hom}_R(P_2, N) \xrightarrow{d_3^*} \cdots $$
* **映射定义：** $d_n^*(\phi) = \phi \circ d_n$，其中 $\phi \in \text{Hom}_R(P_{n-1}, N)$。

**步骤 3：取上同调群**
计算该余链复形在第 $n$ 个位置的同调：
$$ \text{Ext}_R^n(M, N) = \frac{\ker(d_{n+1}^*)}{\text{im}(d_n^*)} $$

---

### 途径 B：分解右变元 $N$ (内射分解法)

利用 $\text{Hom}_R(M, -)$ 的协变性。

**步骤 1：截断复形**
去掉内射分解正合列中的目标模 $N$，得到余链复形 $I^\bullet$（此时在 $I^0$ 处不再正合）：
$$ 0 \to I^0 \xrightarrow{d^0} I^1 \xrightarrow{d^1} I^2 \xrightarrow{d^2} \cdots $$

**步骤 2：施加 Hom 函子**
对上述复形施加协变函子 $\text{Hom}_R(M, -)$，箭头方向保持不变：
$$ 0 \to \text{Hom}_R(M, I^0) \xrightarrow{d_*^0} \text{Hom}_R(M, I^1) \xrightarrow{d_*^1} \text{Hom}_R(M, I^2) \xrightarrow{d_*^2} \cdots $$
* **映射定义：** $d_*^n(\psi) = d^n \circ \psi$，其中 $\psi \in \text{Hom}_R(M, I^n)$。

**步骤 3：取上同调群**
计算该复形在第 $n$ 个位置的同调：
$$ \text{Ext}_R^n(M, N) = \frac{\ker(d_*^n)}{\text{im}(d_*^{n-1})} $$

---

## 3. 核心定理与应用准则

> [!tip] 平衡定理 (Isomorphism)
> 对于任意 $R$-模 $M, N$ 以及任意正整数 $n$，通过途径 A 计算得到的结果与通过途径 B 计算得到的结果是**典范同构**的：
> $$ \frac{\ker(d_{n+1}^*)}{\text{im}(d_n^*)} \cong \frac{\ker(d_*^n)}{\text{im}(d_*^{n-1})} $$
> 
> **实战指导意义：** 在具体计算 $\text{Ext}_R^n(M, N)$ 时，你拥有完全的自由度。如果 $M$ 看起来更容易构造出简洁的投射分解（例如有限生成自由模的商），就走途径 A；如果 $N$ 的内射分解更明显，就走途径 B。

> [!note] 阶数与平凡性
> * $\text{Ext}_R^0(M, N) \cong \text{Hom}_R(M, N)$。
> * 如果 $M$ 是投射模，对于所有 $n \ge 1$，$\text{Ext}_R^n(M, N) = 0$。
> * 如果 $N$ 是内射模，对于所有 $n \ge 1$，$\text{Ext}_R^n(M, N) = 0$。