# 有限型态射 (Morphism of Finite Type)

> [!abstract] 严谨定义
> 设 $f: X \to Y$ 是一个概形态射。
> 1. **局部有限型 (Locally of finite type)**：存在 $Y$ 的一个仿射开覆盖 $V_i = \text{Spec}(B_i)$，并且对于每个 $i$，$f^{-1}(V_i)$ 可以被仿射开集 $U_{ij} = \text{Spec}(A_{ij})$ 覆盖，使得每一个 $A_{ij}$ 作为 $B_i$-代数是**有限生成的 (Finitely Generated)**。
> 2. **有限型 (Finite type)**：如果 $f$ 既是局部有限型的，又是**拟紧的**（即每个 $f^{-1}(V_i)$ 能被**有限个** $U_{ij}$ 覆盖），则称 $f$ 为有限型态射。

## 1. 相关的进阶定义：有限表现 (Finite Presentation)
- **代数基础**：一个 $B$-代数 $A$ 是有限表现的，如果它不仅是由有限个元素生成的，而且它们之间的**关系（Relations的理想）**也是有限生成的。即 $A \cong B[x_1, \dots, x_n] / (f_1, \dots, f_m)$。
- **几何定义**：如果 $A_{ij}$ 作为 $B_i$-代数是有限表现的，则称态射是**局部有限表现的**。结合拟紧性与拟分离性，得到**有限表现态射**。
*(注：当底空间 $Y$ 是 [[诺特概形 (Noetherian Scheme)]] 时，有限型与有限表现是绝对等价的。)*

## 2. 几何意义
“有限型”排除了具有无穷维坐标的空间或需要无限多个变量的多项式环。所有在代数闭域 $k$ 上定义的 [[古典代数簇 (Classical Algebraic Variety)]] 对应的结构态射 $X \to \text{Spec}(k)$ 都必然是有限型态射。

**前置链接**：[[拟紧概形 (Quasi-compact Scheme)]]