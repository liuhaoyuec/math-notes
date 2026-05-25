# 抽象代数簇 (Abstract Algebraic Variety)

> [!abstract] 严谨定义 (基于 Weil 的粘合构造)
> **抽象代数簇**本质上与 [[古典代数簇 (Classical Algebraic Variety)]] 是等价概念，但强调其**构造方式**：它是不依赖于任何外部射影空间 $\mathbb{P}^n_k$ 嵌入，纯粹通过粘合局部的 [[仿射簇 (Affine Variety)]] 得到的几何对象。

## 严密构造过程
1. **数据准备**：给定有限个仿射簇 $V_1, \dots, V_m$。
2. **粘合数据 (Gluing Data)**：对于每一对 $(i, j)$，给定 $V_i$ 中的 Zariski 开集 $U_{ij}$ 和 $V_j$ 中的 Zariski 开集 $U_{ji}$，以及一个古典态射级别的同构 $\phi_{ij}: U_{ij} \xrightarrow{\sim} U_{ji}$。
3. **相容性条件 (Cocycle Condition)**：
   - 反身性：$\phi_{ii} = \text{id}_{V_i}$
   - 对称性：$\phi_{ji} = \phi_{ij}^{-1}$
   - 传递性：在三重交集 $U_{ij} \cap U_{ik}$ 上有 $\phi_{jk} \circ \phi_{ij} = \phi_{ik}$。
4. **生成空间**：将不交并 $\bigsqcup V_i$ 按照等价关系 $x \sim \phi_{ij}(x)$ 进行商拓扑粘合，得到拓扑空间 $X$。
5. **分离性审查**：如果得到的 $X$ 满足对角线闭合条件（分离性），则 $X$ 就是一个合法的抽象簇。

> [!info] 存在性与意义
> Nagata 证明了存在满足上述所有公理，但绝对无法嵌入任何 $\mathbb{P}^n_k$ 的抽象完备簇（如 Nagata 曲面）。抽象簇的定义彻底将代数几何从外在坐标解放为内在流形。