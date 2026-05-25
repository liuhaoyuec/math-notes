# 模范畴 (R-Mod Category)

> [!abstract] 严谨定义
> 设 $R$ 为一个含幺环。**左 $R$-模范畴**，记作 $R\text{-}\mathbf{Mod}$。
> - **对象 (Objects)**：所有的左 $R$-模 (Left $R$-modules)。
> - **态射 (Morphisms)**：$R$-线性映射 ( $R$-linear Maps )，即满足 $f(rx+y) = rf(x)+f(y)$ 的阿贝尔群同态。

## 核心性质与同调代数母体
$R\text{-}\mathbf{Mod}$ 是完美的 **阿贝尔范畴 (Abelian Category)**，它是所有线性代数与同调代数展开的舞台。
- **特例**：当 $R = \mathbb{Z}$ 时，$R\text{-}\mathbf{Mod}$ 严格等价于 [[阿贝尔群范畴 (Ab Category)]]；当 $R$ 为域 $k$ 时，它就是**向量空间范畴 $\mathbf{Vect}_k$**。
- **极限与余极限**：它拥有所有的小极限（如核、直积）和小余极限（如上核、直和）。
- **张量积与内同态**：如果 $R$ 是交换环，模范畴还拥有张量积 $\otimes_R$ 和内同态 $\text{Hom}_R(-, -)$，构成一个闭幺半范畴 (Closed Monoidal Category)。