# 规范层 (Canonical Sheaf)

> [!abstract] 严谨定义
> 设 $X$ 是定义在代数闭域 $k$ 上的、纯维数为 $n$ 的**平滑代数簇**（或正则 $k$-概形）。
> $X$ 的**规范层 $\omega_X$** 被严密定义为相对微分层 $\Omega^1_{X/k}$ 的**第 $n$ 阶外幂 (Top Exterior Power)**：
> $$ \omega_X := \bigwedge^n \Omega^1_{X/k} $$

## 1. 代数与几何性质
- **可逆层 (线丛)**：因为 $X$ 是 $n$ 维平滑簇，$\Omega^1_{X/k}$ 是一个秩为 $n$ 的局部自由层。在线性代数中，一个 $n$ 维向量空间的第 $n$ 阶外代数的维数必然为 $\binom{n}{n} = 1$。因此，$\omega_X$ 是一个秩处处为 1 的局部自由层，即 [[可逆层 (Invertible Sheaf)]]。
- **最高阶微分形式**：$\omega_X$ 的全局截面 $H^0(X, \omega_X)$ 构成了 $X$ 上所有处处正则的全局 $n$-形式（Global Regular $n$-forms）的空间。例如在局部坐标 $x_1, \dots, x_n$ 下，其元素形如 $f(x) dx_1 \wedge \dots \wedge dx_n$。

## 2. 几何亏格 (Geometric Genus) 的最终定义
对于 $n$ 维平滑射影簇，其**几何亏格 $p_g$** 被极其严密地定义为规范层全局截面的维数：
$$ p_g(X) := \dim_k H^0(X, \omega_X) $$
对于曲线 ($n=1$)，$\omega_X = \Omega^1_{X/k}$ 本身就是线丛。

**进阶链接**：规范层是触发同调代数“镜像对称”的核心扭结，见 [[塞尔对偶定理 (Serre Duality Theorem)]]。