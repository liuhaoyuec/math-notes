# 张量积与内同态伴随对 (Tensor ⊣ Hom Adjunction)

> [!abstract] 严谨定义
> 设 $R$ 是一个交换含幺环。在 [[模范畴 (R-Mod Category)]] 中，固定一个 $R$-模 $N$。
> 存在一对极其重要的伴随函子：
> - **左伴随函子**：张量积函子 $- \otimes_R N: R\text{-}\mathbf{Mod} \to R\text{-}\mathbf{Mod}$。
> - **右伴随函子**：内同态函子 $\text{Hom}_R(N, -): R\text{-}\mathbf{Mod} \to R\text{-}\mathbf{Mod}$。
> 
> **伴随同构**：对于任意 $R$-模 $M$ 和 $P$，存在双函子自然的阿贝尔群同构：
> $$\text{Hom}_R(M \otimes_R N, P) \cong \text{Hom}_R(M, \text{Hom}_R(N, P))$$

## 1. 伴随关系的极强代数推论 (连续性定理的应用)
根据范畴论的伴随极限保持定理（左伴随保余极限，右伴随保极限）：
- **张量积 $- \otimes_R N$ 必定保持所有的余极限 (Colimits)**。这意味着它与直和交换（$(\bigoplus M_i) \otimes N \cong \bigoplus (M_i \otimes N)$），并且它是**右正合的 (Right Exact)**。
- **内同态 $\text{Hom}_R(N, -)$ 必定保持所有的极限 (Limits)**。这意味着它与直积交换，并且它是**左正合的 (Left Exact)**。

## 2. 同调代数的基石
正是因为张量积和 Hom 函子分别是右正合和左正合的（且通常不完全正合），我们才需要对它们取**左导函子 (Tor)** 和 **右导函子 (Ext)**。整个同调代数的建立，完全是这对伴随关系在非正合性上的自然延展。