---
tags:
  - 范畴论/伴随
  - 代数/模论
aliases:
  - Ab与R-Mod的伴随对
---
# Ab 与 R-Mod 的自由-遗忘伴随对

注：已知阿贝尔群范畴 $\mathbf{Ab}$ 实际上等价于整数环上的模范畴 $\mathbf{\mathbb{Z}\text{-}Mod}$。在这个伴随中，我们引入一个任意环 $R$。

## functors (函子对)
- **右伴随 (限制/遗忘函子)** $U: \mathbf{R\text{-}Mod} \to \mathbf{Ab}$
  - **作用**：给定一个 $R$-模 $M$，遗忘它的 $R$-标量乘法结构，只保留底层的阿贝尔群加法结构（即 $\mathbb{Z}$-模结构）。
- **左伴随 (标量扩张/自由函子)** $F: \mathbf{Ab} \to \mathbf{R\text{-}Mod}$
  - **作用**：给定一个阿贝尔群 $A$，通过张量积进行**标量扩张 (Extension of Scalars)**，构造出自由的 $R$-模 $R \otimes_{\mathbb{Z}} A$。

## 伴随同构 (Adjunction Isomorphism)
$$Hom_{\mathbf{R\text{-}Mod}}(R \otimes_{\mathbb{Z}} A, M) \cong Hom_{\mathbf{Ab}}(A, U(M))$$

**直观理解**：
要给一个通过“标量扩张”得到的 $R$-模定义线性映射，等价于在这个模的“原始阿贝尔群骨架”上定义一个底层的阿贝尔群同态。张量积的泛性质会自动帮你把 $R$-标量乘法的关系捋顺。

## 复合关系
- 向上复合：追溯回 [[Grp与Ab的伴随对]] 和 [[Set与Grp的伴随对]]，可以揭示从纯集合一步生成自由 $R$-模（以集合为基的 $R$-向量空间）的复合左伴随。
- 向下复合：准备进入拥有内部乘法结构的环范畴，即 [[R-Mod与Ring的伴随对]]（张量代数）。