# 环范畴 (Ring Category)

> [!abstract] 严谨定义
> **环范畴**，记作 $\mathbf{Ring}$（通常在现代代数中默认指**含幺环**）。
> - **对象 (Objects)**：所有带有乘法单位元 $1$ 的结合环 (Unital Associative Rings)。
> - **态射 (Morphisms)**：保单位元的环同态 (Unital Ring Homomorphisms)，即必须满足 $f(x+y)=f(x)+f(y)$，$f(xy)=f(x)f(y)$，且**必须满足 $f(1_R) = 1_S$**。

## 核心性质
- **始对象**：整数环 $\mathbb{Z}$。（因为对于任何环 $R$，存在唯一的环同态 $\mathbb{Z} \to R$，即 $n \mapsto n \cdot 1_R$）。
- **终对象**：零环 $\{0\}$（注意：在零环中 $1=0$。如果有非零环映射到零环，它依然合法）。
- **态射的极度病态**：在 $\mathbf{Ring}$ 中，满态射 (Epimorphism) **不一定**是满射！
  *(经典反例：包含映射 $i: \mathbb{Z} \hookrightarrow \mathbb{Q}$ 是一个满态射。因为对于任何两个环同态 $f, g: \mathbb{Q} \to R$，只要它们在 $\mathbb{Z}$ 上相等，它们在有理数域上也必定相等。)*