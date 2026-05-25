# $t$ 函子：从古典簇到概形的范畴映射

> [!abstract] 范畴等价定理
> 设 $\mathbf{Var}_k$ 为代数闭域 $k$ 上的 [[古典代数簇 (Classical Algebraic Variety)]] 范畴。
> 设 $\mathbf{Sch}_k$ 为 $k$-概形范畴。
> $t$ 函子给出了 $\mathbf{Var}_k$ 到 $\mathbf{Sch}_k$ 中**有限型、分离、整概形 (Integral, Separated, Finite Type over $k$)** 子范畴的**完全等价**。

## 1. 对象的拉回 (Lifting of Objects)
对于任意古典簇 $(V, \mathcal{O}_V)$，概形 $t(V) = (X, \mathcal{O}_X)$ 的严格代数化如下：
- **拓扑底层 $X$**：集合元素定义为 $V$ 的所有非空不可约闭子集（将子簇转化为点，即一般点）。
- **Zariski 拓扑**：闭集基定义为 $t(Z) = \{Y \in X \mid Y \subseteq Z\}$，其中 $Z$ 是 $V$ 中的闭集。
- **结构层 $\mathcal{O}_X$**：由于存在自然连续开映射 $\alpha: V \to X$，结构层直接定义为层的前推：$\mathcal{O}_X = \alpha_* \mathcal{O}_V$，即[[正则函数层]]。
*(注：根据 [[古典代数簇 (Classical Algebraic Variety)]] 的局部仿射性公理，$t(V)$ 必然可以被仿射概形 $\text{Spec}(A_i)$ 覆盖，从而严格成为一个概形。)*

## 2. 态射的拉回 (Lifting of Morphisms)
设 $f: V \to W$ 是古典簇之间的态射。$t(f): t(V) \to t(W)$ 的严谨构造如下：
- **拓扑连续映射的拉回**：
  对于 $t(V)$ 中的任意点 $Y$（即 $V$ 中的不可约闭集），其在 $t(W)$ 中的像被定义为 $f(Y)$ 在 $W$ 中的 Zariski 闭包：
  $$ t(f)(Y) := \overline{f(Y)} $$
- **局部环空间同态的拉回**：
  由于 $\alpha$ 给出了开集的双射，对于 $t(W)$ 的任意开集 $U^*$（对应 $W$ 中的开集 $U$），概形层面的拉回同态：
  $$ t(f)^\#: \mathcal{O}_{t(W)}(U^*) \to \mathcal{O}_{t(V)}(t(f)^{-1}(U^*)) $$
  严格等同于古典层面的正则函数拉回：
  $$ f^\#: \mathcal{O}_W(U) \to \mathcal{O}_V(f^{-1}(U)) $$

> [!check] 全忠实性 (Fully Faithfulness) 的本质
> 态射的拉回证明了：概形态射的代数结构（局部环同态）**完全由古典簇上的正则函数拉回（函数复合）决定**。没有任何信息的增加或丢失，概形论只是提供了一个包含了“一般点”以使得代数运算更加完备的底层拓扑容器。