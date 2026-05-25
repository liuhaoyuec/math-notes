# 层的正像与逆像伴随对 (Direct & Inverse Image Adjunction)

> [!abstract] 严谨定义
> 设 $f: X \to Y$ 是拓扑空间之间的连续映射（在代数几何中为概形态射）。这诱导了两个极其重要的层范畴之间的伴随函子：
> - **右伴随函子**：正像 (Direct Image / Pushforward) $f_*: \mathbf{Sh}(X) \to \mathbf{Sh}(Y)$。
>   定义为：$f_*\mathcal{F}(V) = \mathcal{F}(f^{-1}(V))$。
> - **左伴随函子**：逆像 (Inverse Image / Pullback) $f^*: \mathbf{Sh}(Y) \to \mathbf{Sh}(X)$。
>   定义为预层极限 $U \mapsto \varinjlim_{V \supseteq f(U)} \mathcal{G}(V)$ 的**层化**。
> 
> **伴随同构**：对于 $X$ 上的层 $\mathcal{F}$ 和 $Y$ 上的层 $\mathcal{G}$：
> $$\text{Hom}_{\mathbf{Sh}(X)}(f^*\mathcal{G}, \mathcal{F}) \cong \text{Hom}_{\mathbf{Sh}(Y)}(\mathcal{G}, f_*\mathcal{F})$$

## 1. 极限保持定理的几何显现
- **$f_*$ 作为右伴随，必定左正合**：正像函子 $f_*$ 保持核，但不保持满射。正因为 $f_*$ 破坏了右正合性，我们才必须定义它的右导函子——**高阶正像 (Higher Direct Image) $R^i f_*$**。*(注：当 $Y$ 是单点空间时，$f_*$ 严格退化为全局截面函子 $\Gamma(X, -)$，高阶正像严密退化为 [[层上同调 (Sheaf Cohomology)]] $H^i(X, -)$)*。
- **$f^*$ 作为左伴随，必定右正合**：逆像函子 $f^*$ 保持上核与张量积。它把目标空间 $Y$ 的几何结构（如纤维积）完美且毫无误差地拉回到源空间 $X$。

## 2. 相对概形理论的基石
在 $\mathcal{O}_X$-模的框架下，纯拓扑的逆像 $f^{-1}$ 会被升级为代数拉回 $f^*\mathcal{G} = f^{-1}\mathcal{G} \otimes_{f^{-1}\mathcal{O}_Y} \mathcal{O}_X$。这对伴随关系控制了代数几何中所有基变换 (Base Change) 的同调推演。