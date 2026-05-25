
---
tags:
  - 范畴论/伴随
  - 代数/交换环
aliases:
  - Ring与CRing的伴随对
---
# Ring 与 CRing 的自由-遗忘伴随对

和 `Grp -> Ab` 的逻辑一模一样，这里是仅仅遗忘“交换律”公理的伴随对。

## functors (函子对)
- **右伴随 (包含/遗忘函子)** $U: \mathbf{CRing} \to \mathbf{Ring}$
  - **作用**：交换环本身就是环。这里“遗忘”了乘法交换律，把交换环当作普通的（可能非交换的）环来看待。这是一个**全忠实嵌入**。
- **左伴随 (交换化/自由函子)** $F: \mathbf{Ring} \to \mathbf{CRing}$
  - **作用**：给定一个非交换环 $R$，强行赋予它乘法交换律。构造方法是找到由所有“换位子” $ab - ba$（其中 $a,b \in R$）生成的双侧理想 $I$，然后做商环：
    $$R^{ab} = R / \langle ab - ba \rangle$$
  - 这就得到了包络这个非交换环的“最自由的”交换环。

## 伴随同构 (Adjunction Isomorphism)
$$Hom_{\mathbf{CRing}}(R^{ab}, C) \cong Hom_{\mathbf{Ring}}(R, U(C))$$

**直观理解**：
任何从非交换环 $R$ 映射到交换环 $C$ 的环同态，必然会把所有 $ab-ba$ 的形式映射为 $0$（因为目标环里 $f(a)f(b) = f(b)f(a)$）。因此，这个同态必然要“穿过”那个做过商的交换化环 $R^{ab}$。