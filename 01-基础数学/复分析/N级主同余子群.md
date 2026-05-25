# $N$ 级主同余子群 $\Gamma(N)$ (Principal Congruence Subgroup)

**定义**：
给定正整数 $N$，$\Gamma(N)$ 包含所有在模 $N$ 意义下与单位矩阵同余的 $SL_2(\mathbb{Z})$ 矩阵：
$$\Gamma(N) = \left\{ \begin{pmatrix} a & b \\ c & d \end{pmatrix} \in SL_2(\mathbb{Z}) \mathrel{\Bigg|} \begin{pmatrix} a & b \\ c & d \end{pmatrix} \equiv \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix} \pmod N \right\}$$
等价条件：$a \equiv 1 \pmod N$，$d \equiv 1 \pmod N$，且 $b \equiv 0 \pmod N$，$c \equiv 0 \pmod N$。

**作用**：
这是所有同余子群的基础。任何包含 $\Gamma(N)$ 的 $SL_2(\mathbb{Z})$ 的子群，都被称为一个 **$N$ 级同余子群**。当 $N=1$ 时，$\Gamma(1) = SL_2(\mathbb{Z})$。