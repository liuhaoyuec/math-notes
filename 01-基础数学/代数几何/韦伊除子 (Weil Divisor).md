# 韦伊除子 (Weil Divisor)

> [!abstract] 严谨定义 (几何除子)
> 设 $X$ 是一个满足以下条件的概形：**诺特的 (Noetherian)**、**整的 (Integral)**、且**分离的 (Separated)**，并且**在余维数 1 处是正则的 (Regular in codimension 1)**。
> $X$ 上的一个**韦伊除子 (Weil Divisor)** $D$ 是 $X$ 的所有余维数为 1 的素除子 (Prime Divisors) 的**形式有限整系数线性组合**：
> $$D = \sum_{i} n_i Y_i$$
> 其中 $Y_i$ 是 $X$ 的不可约闭子概形且其 Krull 维数满足 $\text{codim}(Y_i, X) = 1$，$n_i \in \mathbb{Z}$，且仅有有限个 $n_i \neq 0$。

## 1. 核心概念与分类
- **素除子 (Prime Divisor)**：系数为 1 且只有一个闭子概形的除子。
- **有效除子 (Effective Divisor)**：如果所有系数 $n_i \ge 0$，记作 $D \ge 0$。
- **除子群 $\text{Div}(X)$**：所有韦伊除子构成的自由阿贝尔群。

## 2. 主除子 (Principal Divisor) 与除子类群
对于有理函数域 $K(X)$ 中的任意非零有理函数 $f \in K(X)^\times$，可以严谨定义其在素除子 $Y$ 处的**离散赋值 (Discrete Valuation)** $v_Y(f)$（即在该处零点或极点的阶数）。
- **主除子**：由有理函数 $f$ 定义的除子：$\text{div}(f) = \sum_{Y} v_Y(f) Y$。
- **线性等价 (Linear Equivalence)**：如果 $D_1 - D_2 = \text{div}(f)$，则称它们线性等价，记作 $D_1 \sim D_2$。
- **除子类群 (Class Group)**：$\text{Cl}(X) = \text{Div}(X) / \text{Prin}(X)$。它是衡量概形 $X$ 上的坐标环偏离“唯一分解整环 (UFD)”程度的几何不变量（若 $X = \text{Spec}(A)$，则 $\text{Cl}(X)=0 \iff A$ 是 UFD）。

**进阶链接**：与 [[卡地亚除子 (Cartier Divisor)]] 的等价性定理。