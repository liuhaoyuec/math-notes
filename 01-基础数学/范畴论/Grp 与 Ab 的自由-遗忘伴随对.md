---
tags:
  - 范畴论/伴随
  - 代数/阿贝尔群
aliases:
  - Grp与Ab的伴随对
---
# Grp 与 Ab 的自由-遗忘伴随对

这里“遗忘”的不是运算结构，而是公理（交换律）。

## functors (函子对)
- **右伴随 (包含/遗忘函子)** $U: \mathbf{Ab} \to \mathbf{Grp}$
  - **作用**：阿贝尔群本身就是群，这里只是“遗忘”了交换律，将其视为普通群。这是一个**全忠实嵌入 (Fully Faithful Embedding)**。
- **左伴随 (交换化/自由函子)** $F: \mathbf{Grp} \to \mathbf{Ab}$
  - **作用**：给定任意群 $G$，强行赋给它交换律。构造方法是模掉 $G$ 的换位子群 $[G,G]$（由所有 $aba^{-1}b^{-1}$ 形式的元素生成的正规子群），得到**阿贝尔化群 (Abelianization)** $G^{ab} = G/[G,G]$。

## 伴随同构 (Adjunction Isomorphism)
$$Hom_{\mathbf{Ab}}(G^{ab}, A) \cong Hom_{\mathbf{Grp}}(G, U(A))$$

**直观理解**：
任何从非交换群 $G$ 到交换群 $A$ 的群同态，都会自动把换位子映射到单位元（因为目标是交换的）。因此，这个同态必然且唯一地“分解”经过它的阿贝尔化 $G^{ab}$。

## 复合关系
- 向上复合：结合 [[Set与Grp的伴随对]]，我们可以一步从集合构造出自由阿贝尔群 $\bigoplus \mathbb{Z}$。
- 向下复合：阿贝尔群自然等价于 $\mathbb{Z}$-模，这就衔接到了 [[Ab与R-Mod的伴随对]]。