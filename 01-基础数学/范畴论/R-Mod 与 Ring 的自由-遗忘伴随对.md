---
tags:
  - 范畴论/伴随
  - 代数/环论
  - 张量代数
aliases:
  - R-Mod与Ring的伴随对
---
---
tags:
  - 范畴论/伴随
  - 代数/环论
  - 代数/模论
aliases:
  - R-Mod与R-Alg的伴随对
---
# R-Mod 与 R-Alg 的自由-遗忘伴随对

注：严格来说，任意模的张量代数对应的上层范畴不是普通环范畴 (Ring)，而是 $R$-代数范畴 (R-Alg)。只有当 $R=\mathbb{Z}$ 时，目标范畴才是所有环。

## functors (函子对)
- **右伴随 (遗忘函子)** $U: \mathbf{R\text{-Alg}} \to \mathbf{R\text{-Mod}}$
  - **作用**：给定一个 $R$-代数（一个环，且带有兼容的 $R$-标量乘法），遗忘它的“内部乘法”结构，仅仅保留它的加法和 $R$-标量乘法，使其退化为一个纯粹的 $R$-模。
- **左伴随 (张量代数/自由函子)** $T: \mathbf{R\text{-Mod}} \to \mathbf{R\text{-Alg}}$
  - **作用**：给定一个 $R$-模 $M$，我们要强行给它无中生有出一个“内部乘法”。做法是构造**张量代数 (Tensor Algebra)**：
    $$T(M) = R \oplus M \oplus (M \otimes_R M) \oplus (M \otimes_R M \otimes_R M) \oplus \dots$$
  - 把不同阶的张量拼接起来作为乘法，这就成了一个由模 $M$ 自由生成的 $R$-代数。

## 伴随同构 (Adjunction Isomorphism)
$$Hom_{\mathbf{R\text{-Alg}}}(T(M), A) \cong Hom_{\mathbf{R\text{-Mod}}}(M, U(A))$$

**直观理解**：
要定义一个从张量代数 $T(M)$ 到任意 $R$-代数 $A$ 的代数同态，你只需要知道怎么把底层的模 $M$ 通过 $R$-线性映射送过去即可。高阶的张量乘法会被泛性质自动约束。