# 标量扩张与限制伴随对 (Extension ⊣ Restriction of Scalars)

> [!abstract] 严谨定义
> 设 $\phi: A \to B$ 是交换环之间的一个环同态。（在几何上对应于仿射概形态射 $f: \text{Spec}(B) \to \text{Spec}(A)$）。
> 这诱导了模范畴之间的核心伴随对：
> - **右伴随函子**：标量限制 (Restriction of Scalars) $\phi_*: B\text{-}\mathbf{Mod} \to A\text{-}\mathbf{Mod}$。它将一个 $B$-模 $M$ 直接视为 $A$-模（通过作用 $a \cdot m = \phi(a)m$）。
> - **左伴随函子**：标量扩张 (Extension of Scalars) $\phi^*: A\text{-}\mathbf{Mod} \to B\text{-}\mathbf{Mod}$。它通过张量积定义：$N \mapsto N \otimes_A B$。
> 
> **伴随同构**：对于 $A$-模 $N$ 和 $B$-模 $M$：
> $$\text{Hom}_B(N \otimes_A B, M) \cong \text{Hom}_A(N, \phi_* M)$$

## 1. 代数与几何的完美镜像 (Grothendieck 的对译)
这对代数伴随函子，与 [[层的正像与逆像伴随对 (Direct & Inverse Image Adjunction)]] 是**绝对且严密的镜像**。
- 代数中的标量限制 $\phi_* M$，严密对应于几何中拟凝聚层的正像 $f_* \tilde{M}$。
- 代数中的标量扩张 $N \otimes_A B$，严密对应于几何中拟凝聚层的逆像 $f^* \tilde{N}$。
- 伴随关系的双射公式，正是 $f^* \dashv f_*$ 在仿射概形上的纯代数显现。

## 2. 几何意义：纤维的计算
当考察态射 $f: X \to Y$ 在某点 $y \in Y$ 处的纤维时（即拉回到剩余域 $k(y)$），其本质就是沿着环同态 $\mathcal{O}_{Y,y} \to k(y)$ 进行标量扩张（取张量积）。这解释了为什么张量积在代数几何中无处不在——它就是“几何截取/基变换”的代数执行者。