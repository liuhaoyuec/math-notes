# Eisenstein级数 (Eisenstein Series)

**定义**：对于复平面上的[[复格]] $\Lambda$，当整数 $k \geq 3$ 时，与其相关的 $k$ 阶 **Eisenstein 级数** 定义为所有非零格点的 $k$ 次方倒数之和：
$$G_k(\Lambda) = \sum_{\omega \in \Lambda^*} \frac{1}{\omega^k}$$

**性质**：
1. **绝对收敛性**：当 $k > 2$ 时，该二重级数绝对收敛，因此级数的值与求和顺序无关。
2. **奇数阶为零**：如果 $k$ 是奇数，由于格具有中心对称性 ($\omega \in \Lambda^* \iff -\omega \in \Lambda^*$)，有 $\omega^{-k} + (-\omega)^{-k} = 0$，因此对于所有奇数 $k$，$G_k = 0$。
3. **关联不变量**：在椭圆曲线的理论中，最重要的是 $k=4$ 和 $k=6$ 的级数，它们构成了 Weierstrass 椭圆曲线方程中的系数（称为模不变量）：
   * $g_2 = 60 G_4$
   * $g_3 = 140 G_6$