# 分离概形 (Separated Scheme)



> [!abstract] 严谨定义
> 设 $f: X \to S$ 是一个概形态射。定义**对角态射 (Diagonal Morphism)** $\Delta: X \to X \times_S X$ 为诱导自恒等映射 $\text{id}_X$ 的泛性质态射。
> 如果对角态射 $\Delta$ 是一个**闭浸入 (Closed Immersion)**，则称态射 $f$ 是**分离的**。
> 如果 $X \to \text{Spec}(\mathbb{Z})$ 是分离的，我们绝对地称 $X$ 是一个**分离概形**。

## 1. 前置知识
- **纤维积 (Fiber Product)**：概形范畴中的拉回结构 $X \times_S Y$，它泛化了集合的笛卡尔积和代数的张量积（$A \otimes_R B$）。
- **闭浸入 (Closed Immersion)**：一个态射 $i: Z \to X$，它在拓扑上是闭映射且像同胚于 $Z$，在层论上诱导的结构层同态 $\mathcal{O}_X \to i_* \mathcal{O}_Z$ 是满射。

## 2. 为什么需要分离性？(代数几何的 Hausdorff 条件)
由于 Zariski 拓扑极弱，概形通常不是 Hausdorff 空间。
在一般拓扑学中，一个空间 $Y$ 是 Hausdorff 的 $\iff$ 对角线集 $\Delta(Y) \subset Y \times Y$ 是闭集。
Grothendieck 直接将这个拓扑性质翻译成了概形范畴中的代数条件（对角态射为闭浸入）。
**反例**：经典的“带两个原点的仿射直线”。由于在原点处的极限不唯一，它的对角线在乘积空间中不是闭集，因此它是非分离的。

## 3. 分离性的严谨判定 (Valuative Criterion for Separatedness)
**赋值判别法**是检验分离性的极其强大的工具：
对于任意赋值环 $R$（设其分式域为 $K$），给出图表交换条件。分离性严格等价于：从 $\text{Spec}(K)$ 到 $X$ 的态射，最多只能有一种方式延拓为从 $\text{Spec}(R)$ 到 $X$ 的态射。
**几何意义**：曲线上缺失的点不能被“填补”两次（极限必须唯一）。所有的 [[古典代数簇 (Classical Algebraic Variety)]] 都强制要求是分离概形。