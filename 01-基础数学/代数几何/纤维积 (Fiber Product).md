# 纤维积 (Fiber Product)



> [!abstract] 严谨定义 (基于泛性质 Universal Property)
> 设 $f: X \to S$ 和 $g: Y \to S$ 是概形范畴 $\mathbf{Sch}$ 中的两个态射（即 $X$ 和 $Y$ 都是 $S$-概形）。
> 它们在 $S$ 上的**纤维积**是一个概形，记作 $X \times_S Y$，并配备两个**投影态射** $p_1: X \times_S Y \to X$ 和 $p_2: X \times_S Y \to Y$，满足以下条件：
> 1. **交换性**：$f \circ p_1 = g \circ p_2$。
> 2. **泛性质 (Universal Property)**：对于任意概形 $Z$ 以及任意两个态射 $q_1: Z \to X$ 和 $q_2: Z \to Y$ 满足 $f \circ q_1 = g \circ q_2$，**存在唯一**的一个态射 $h: Z \to X \times_S Y$，使得 $q_1 = p_1 \circ h$ 且 $q_2 = p_2 \circ h$。

## 1. 交换图 (Commutative Diagram)
在代数几何中，泛性质通常用严谨的交换图表示。对于上述定义，图表如下：
$$
\begin{array}{ccc}
Z & \xrightarrow{\exists ! h} & X \times_S Y & \xrightarrow{p_2} & Y \\
& \searrow_{q_1} & \downarrow^{p_1} & & \downarrow^{g} \\
& & X & \xrightarrow{f} & S
\end{array}
$$
*注：只要泛性质被满足，纤维积在同构意义下是**绝对唯一**的。*

## 2. 仿射概形的显式构造 (张量积的几何化)
要证明纤维积总是存在，我们首先看仿射情况。
设 $S = \text{Spec}(R)$，$X = \text{Spec}(A)$，$Y = \text{Spec}(B)$。
态射 $X \to S$ 和 $Y \to S$ 分别对应环同态 $R \to A$ 和 $R \to B$。
此时，纤维积的构造严格等价于交换代数中的**张量积 (Tensor Product)**：
$$ \text{Spec}(A) \times_{\text{Spec}(R)} \text{Spec}(B) \cong \text{Spec}(A \otimes_R B) $$
**证明逻辑**：环范畴与仿射概形范畴反变等价。张量积 $A \otimes_R B$ 是 $R$-代数范畴中的推出 (Pushout)，反变过来自然就是仿射概形范畴中的拉回 (Pullback，即纤维积)。

## 3. 整体概形的粘合构造 (Gluing)
对于一般的概形 $X, Y, S$，构造分为两步：
1. **取仿射开覆盖**：用仿射开集 $U_i$ 覆盖 $S$，再用仿射开集覆盖它们在 $X$ 和 $Y$ 中的原像。
2. **局部张量积与粘合**：在每一小块仿射开集上，利用张量积 $A \otimes_R B$ 构造出局部的纤维积概形，然后利用层公理（Sheaf Axioms）和泛性质的唯一性，将这些局部概形严密地沿着交集粘合成一个整体的概形 $X \times_S Y$。



## 4. 极其重要的几何应用

### 4.1 方程组的联立与空间相交 (Intersection)
如果 $X$ 和 $Y$ 都是 $S$ 的闭子概形（由理想层 $\mathcal{I}$ 和 $\mathcal{J}$ 定义）。
它们的纤维积 $X \times_S Y$ 严格同构于它们的**图论交集概形**，其对应的理想层就是 $\mathcal{I} + \mathcal{J}$。
*(代数解释：$R/I \otimes_R R/J \cong R/(I+J)$。这严谨地定义了“解非线性方程组”的几何等价物。)*

### 4.2 基变换 (Base Change)
如果 $X \to S$ 是一个以 $S$ 为参数空间（Base）的概形族。给定一个参数空间的变换 $Y \to S$。
纤维积 $X \times_S Y$ 诱导了一个投影 $p_2: X \times_S Y \to Y$。这被称为 $X$ 沿着 $Y \to S$ 的**基变换**。
*(这是代数几何中最常用的操作：将定义在某个域（如 $\mathbb{Q}$）上的概形，提升到更大的域（如 $\mathbb{C}$）上进行研究，即 $X \times_{\text{Spec}(\mathbb{Q})} \text{Spec}(\mathbb{C})$。)*

### 4.3 纤维 (Fibers) 的严谨定义
态射 $f: X \to Y$ 在点 $y \in Y$ 处的“原像”该如何赋予严谨的概形结构？
设 $k(y) = \mathcal{O}_{Y,y}/\mathfrak{m}_y$ 为点 $y$ 的**剩余域 (Residue Field)**。自然存在一个态射 $\text{Spec}(k(y)) \to Y$。
态射 $f$ 在点 $y$ 处的**几何纤维 (Geometric Fiber)** $X_y$ 被严格定义为：
$$ X_y = X \times_Y \text{Spec}(k(y)) $$
这允许我们将任意态射 $X \to Y$ 拆解为无数个定义在各个剩余域上的局部概形进行研究。

**相关链接**：
- 纤维积的对角态射用于严谨定义 [[分离概形 (Separated Scheme)]]。
- 在平坦形变中，纤维的 Hilbert 多项式保持不变，详见 [[平坦态射 (Flat Morphism)]]。