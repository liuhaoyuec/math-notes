# 权 $k$ 格函数与模形式的完美双射（证明）

> [!abstract] 核心提要
> 模形式理论的底层逻辑建立在两个空间的一一对应上：一个是具有齐次性的**格函数空间 $\mathcal{L}_k$**，另一个是具有莫比乌斯变换对称性的**模形式空间 $\mathcal{M}_k$**。本篇笔记将严格证明这两个空间之间的线性同构（双射）。

---

## 1. 核心定义

为了保证推导的严密性，我们首先明确两个空间的数学对象。约定所有涉及的格均具有正定向，即基底 $(\omega_1, \omega_2)$ 满足 $\text{Im}(\omega_1/\omega_2) > 0$。

### 1.1 权 $k$ 的格函数 (Lattice Function of weight $k$)
**定义：** 设 $\mathcal{L}$ 为复平面 $\mathbb{C}$ 上所有格（Lattice）构成的集合。一个定义在 $\mathcal{L}$ 上的复值函数 $F: \mathcal{L} \to \mathbb{C}$，如果满足以下**齐次性条件（Homogeneity）**，则称为权为 $k$ 的格函数：
对于任意非零复数 $\lambda \in \mathbb{C}^\times$ 以及任意格 $\Lambda \in \mathcal{L}$，都有：
$$F(\lambda\Lambda) = \lambda^{-k}F(\Lambda)$$
> *注：这里 $\lambda\Lambda = \{\lambda\omega \mid \omega \in \Lambda\}$ 表示对整个格进行旋转和缩放。函数 $F$ 只依赖于格这个集合本身，不依赖于基底的选取。*

### 1.2 权 $k$ 的模形式 (Modular Form of weight $k$)
**定义（截断版）：** 函数 $f: \mathbb{H} \to \mathbb{C}$ 是上半平面的全纯函数。如果对于任意矩阵 $\begin{pmatrix} a & b \\ c & d \end{pmatrix} \in \text{SL}_2(\mathbb{Z})$，都满足**模变换性质**：
$$f\left(\frac{az+b}{cz+d}\right) = (cz+d)^k f(z)$$
且在尖点处全纯，则称 $f(z)$ 为权为 $k$ 的模形式。

---

## 2. 映射的构造与 Well-definedness（良定性）证明

我们需要在 $\mathcal{L}_k$ 和 $\mathcal{M}_k$ 之间建立两座桥梁：映射 $\Phi$ 和 $\Psi$。

### 2.1 从格函数到模形式（顺向映射 $\Phi$）
定义映射 $\Phi: \mathcal{L}_k \to \mathcal{M}_k$ 如下：
给定一个权为 $k$ 的格函数 $F(\Lambda)$，我们定义上半平面的函数 $f(z)$ 为：
$$f(z) := \Phi(F)(z) = F(\mathbb{Z}z \oplus \mathbb{Z})$$

> [!check] 验证 $\Phi(F)$ 的模变换性质
> 任取 $\begin{pmatrix} a & b \\ c & d \end{pmatrix} \in \text{SL}_2(\mathbb{Z})$。
> $$f\left(\frac{az+b}{cz+d}\right) = F\left(\mathbb{Z}\left(\frac{az+b}{cz+d}\right) \oplus \mathbb{Z}(1)\right)$$
> 作为一个集合，我们可以提取公因子 $\frac{1}{cz+d}$：
> $$= F\left( \frac{1}{cz+d} \Big( \mathbb{Z}(az+b) \oplus \mathbb{Z}(cz+d) \Big) \right)$$
> 因为 $\begin{pmatrix} a & b \\ c & d \end{pmatrix} \in \text{SL}_2(\mathbb{Z})$，整数幺模线性组合不改变格集合本身，即 $\mathbb{Z}(az+b) \oplus \mathbb{Z}(cz+d) = \mathbb{Z}z \oplus \mathbb{Z}$。
> $$= F\left( \frac{1}{cz+d} \Big( \mathbb{Z}z \oplus \mathbb{Z} \Big) \right)$$
> 调用 $F$ 的 $-k$ 次齐次性，其中 $\lambda = \frac{1}{cz+d}$：
> $$= \left(\frac{1}{cz+d}\right)^{-k} F(\mathbb{Z}z \oplus \mathbb{Z}) = (cz+d)^k f(z)$$
> 这证明了由格函数构造出的 $f(z)$ 确实满足模形式的变换性质。

### 2.2 从模形式到格函数（逆向映射 $\Psi$ 与最核心的证明）
定义映射 $\Psi: \mathcal{M}_k \to \mathcal{L}_k$ 如下：
给定一个权为 $k$ 的模形式 $f(z)$，对于任意给定的格 $\Lambda \in \mathcal{L}$，我们**为其任选一组正定向基底** $(\omega_1, \omega_2)$，并由此定义格函数 $F(\Lambda)$ 为：
$$F(\Lambda) := \Psi(f)(\Lambda) = \omega_2^{-k} f\left(\frac{\omega_1}{\omega_2}\right)$$

> [!danger] 核心危机：良定性（Well-definedness）
> 上述定义极其危险！格 $\Lambda$ 本质上是一个客观的**点集**，它拥有无限多组正定向基底。而我们的定义却是强行依赖于其中**某一特定的选取** $(\omega_1, \omega_2)$。
> 如果面对同一个格 $\Lambda$，张三和李四选取了不同的正定向基底，算出来的值不一样，这个函数 $F(\Lambda)$ 就不存在（发生破缺）！
> 因此，我们**必须**证明：无论选取哪一组正定向基底，计算出的 $F$ 值绝对相等。
>

> [!quote] 证明：映射 $\Psi$ 的良定性
> 设同一个正定向格 $\Lambda$ 有两组不同的正定向基底 $(\omega_1, \omega_2)$ 和 $(\omega'_1, \omega'_2)$。
> 由带定向格的性质可知，它们必然通过 $\text{SL}_2(\mathbb{Z})$ 矩阵相联系。设存在 $\begin{pmatrix} a & b \\ c & d \end{pmatrix} \in \text{SL}_2(\mathbb{Z})$，使得：
> $$\omega'_1 = a\omega_1 + b\omega_2$$
> $$\omega'_2 = c\omega_1 + d\omega_2$$
> 
> 现在我们用新基底来计算 $F$ 的值：
> $$F_{\text{新}} = (\omega'_2)^{-k} f\left(\frac{\omega'_1}{\omega'_2}\right)$$
> 毫无保留地代入 $\omega'_1$ 和 $\omega'_2$ 的表达式：
> $$F_{\text{新}} = (c\omega_1 + d\omega_2)^{-k} f\left(\frac{a\omega_1+b\omega_2}{c\omega_1+d\omega_2}\right)$$
> 在括号内外同时强行提出 $\omega_2$：
> $$= \left[\omega_2 \left(c\frac{\omega_1}{\omega_2} + d\right)\right]^{-k} f\left(\frac{a(\omega_1/\omega_2)+b}{c(\omega_1/\omega_2)+d}\right)$$
> 令 $z = \frac{\omega_1}{\omega_2}$，式子化简为：
> $$= \omega_2^{-k} (cz+d)^{-k} f\left(\frac{az+b}{cz+d}\right)$$
> **最惊艳的一步来了：** 因为 $f(z)$ 是权为 $k$ 的模形式，它必定满足 $f(\frac{az+b}{cz+d}) = (cz+d)^k f(z)$。将其代入：
> $$= \omega_2^{-k} (cz+d)^{-k} \cdot \left[ (cz+d)^k f(z) \right]$$
> $$= \omega_2^{-k} f(z)$$
> 将 $z = \frac{\omega_1}{\omega_2}$ 代回：
> $$= \omega_2^{-k} f\left(\frac{\omega_1}{\omega_2}\right) = F_{\text{老}}$$
> 
> **结论：** 无论基底如何变换，计算出的 $F$ 值如磐石般不可动摇。因此，由模形式 $f(z)$ 逆向构造出的格函数 $F(\Lambda)$ 是**绝对良定（Well-defined）**的！

---

## 3. 双射（Bijection）的最终证明

我们已经有了 $\Phi$ 和 $\Psi$ 两个良定的映射，最后只需要证明它们互为逆映射。

### 3.1 证明 $\Phi \circ \Psi = \text{id}_{\mathcal{M}_k}$
任取一个模形式 $f \in \mathcal{M}_k$，先用 $\Psi$ 将其变为格函数 $F$，再用 $\Phi$ 变回模形式 $\tilde{f}$：
$$\tilde{f}(z) = \Phi(F)(z) = F(\mathbb{Z}z \oplus \mathbb{Z})$$
调用 $\Psi$ 的定义（此时基底为 $\omega_1 = z, \omega_2 = 1$）：
$$= 1^{-k} \cdot f\left(\frac{z}{1}\right) = f(z)$$
因此，$\tilde{f} = f$，正向复合是恒等映射。

### 3.2 证明 $\Psi \circ \Phi = \text{id}_{\mathcal{L}_k}$
任取一个格函数 $F \in \mathcal{L}_k$，先用 $\Phi$ 将其变为模形式 $f(z) = F(\mathbb{Z}z \oplus \mathbb{Z})$，再用 $\Psi$ 变回格函数 $\tilde{F}$：
$$\tilde{F}(\Lambda) = \tilde{F}(\mathbb{Z}\omega_1 \oplus \mathbb{Z}\omega_2) = \omega_2^{-k} f\left(\frac{\omega_1}{\omega_2}\right)$$
将 $f$ 的构造定义代入：
$$= \omega_2^{-k} F\left(\mathbb{Z}\left(\frac{\omega_1}{\omega_2}\right) \oplus \mathbb{Z}(1)\right)$$
将常数 $\omega_2^{-k}$ 利用格函数的**齐次性**（令 $\lambda = \omega_2$）放进函数内部：
$$= F\left( \omega_2 \left[ \mathbb{Z}\left(\frac{\omega_1}{\omega_2}\right) \oplus \mathbb{Z}(1) \right] \right)$$
$$= F\left( \mathbb{Z}\omega_1 \oplus \mathbb{Z}\omega_2 \right) = F(\Lambda)$$
因此，$\tilde{F} = F$，逆向复合也是恒等映射。

> [!success] 最终结论
> 综上所述，映射 $\Phi$ 和 $\Psi$ 是互为逆映射的同构桥梁。我们得到：
> **格函数空间 $\mathcal{L}_k$ 与模形式空间 $\mathcal{M}_k$ 存在完美的一一对应（双射）关系。** 这为我们在研究时随时在这两个空间中无缝切换提供了坚实的理论基石。$\blacksquare$