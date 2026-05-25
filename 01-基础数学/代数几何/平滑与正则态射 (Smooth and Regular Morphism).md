# 平滑与正则态射 (Smooth Morphism)

> [!abstract] 严谨定义
> 设 $f: X \to Y$ 是一个概形态射。$f$ 被称为**平滑态射 (Smooth Morphism)**，如果它同时满足：
> 1. 它是局部 [[有限型态射 (Morphism of Finite Type)]] 且局部有限表现的。
> 2. 它是 [[平坦态射 (Flat Morphism)]]。
> 3. 它的**相对微分层 (Sheaf of Relative Differentials)** $\Omega^1_{X/Y}$ 是一个秩等于其相对维数的局部自由层（Locally Free Sheaf），且所有几何纤维都是正则概形。

## 1. 前置知识：凯勒微分层 (Kähler Differentials)
$\Omega^1_{X/Y}$ 严谨地代数化了微分几何中的“余切丛”。对于 $A$-代数 $B$，微分模 $\Omega_{B/A}$ 由所有形式微分 $db$ 构成，模掉莱布尼茨法则（$d(b_1b_2) = b_1db_2 + b_2db_1$）和常数导数为零（$da = 0$）。

## 2. 代数等价定义 (形式平滑性)
根据 Grothendieck 的形式形变理论，$f$ 是平滑的等价于**形式平滑 (Formally Smooth)**：
对于任意的仿射概形 $Z = \text{Spec}(A)$ 及其由幂零理想 $I$ 定义的闭子概形 $Z_0 = \text{Spec}(A/I)$，任何从 $Z_0$ 到 $X$ 的态射（在 $Y$ 上），都必定可以至少一种方式提升为从 $Z$ 到 $X$ 的态射。
*(直观理解：在平滑空间上，不存在被“堵死”而无法无穷小延拓的切向形变。)*

## 3. 几何直觉与正则性
- 平滑态射是微分流形中**淹没 (Submersion)** 在代数几何中的对应物。
- 若基底 $Y = \text{Spec}(k)$（$k$ 为完美域），结构态射 $X \to \text{Spec}(k)$ 平滑严格等价于 $X$ 是一个**正则概形 (Regular Scheme)**。即 $X$ 的所有局部环都是正则局部环（极大理想生成的维数等于克鲁尔维数）。
- 这就是在严谨定义“无奇异点 (Non-singular)”的代数空间。