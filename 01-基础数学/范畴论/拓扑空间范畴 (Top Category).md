# 拓扑空间范畴 (Top Category)

> [!abstract] 严谨定义
> **拓扑空间范畴**，记作 $\mathbf{Top}$。
> - **对象 (Objects)**：所有的拓扑空间 (Topological Spaces)，即对 $(X, \tau)$。
> - **态射 (Morphisms)**：连续映射 (Continuous Maps)，即开集的原像必定是开集。

## 核心性质
- **始对象**：空空间 $\emptyset$。
- **终对象**：单点空间 $\{*\}$。
- **乘积与余乘积**：
  - 乘积 (Product) 对应于赋予了**乘积拓扑 (Product Topology)** 的笛卡尔积。
  - 余乘积 (Coproduct) 对应于赋予了**不交并拓扑 (Disjoint Union Topology)** 的拓扑和。
- **病态的单满性**：在 $\mathbf{Top}$ 中，同构 (Isomorphism) 必须是**同胚 (Homeomorphism)**（即双射且正反均连续）。存在既是单态射又是满态射，但**不是**同构的态射（例如从离散拓扑到密着拓扑的恒等映射）。