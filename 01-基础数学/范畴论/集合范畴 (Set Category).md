# 集合范畴 (Set Category)

> [!abstract] 严谨定义
> **集合范畴**，记作 $\mathbf{Set}$，是所有数学结构的最底层基底。
> - **对象 (Objects)**：所有的集合 (Sets)。
> - **态射 (Morphisms)**：集合之间的全体映射 (Functions)。
> - **复合 (Composition)**：映射的常规复合。

## 核心性质与范畴论地位
- $\mathbf{Set}$ 是一个完备 (Complete) 且余完备 (Cocomplete) 的范畴（即存在所有小极限和小余极限）。
- **终对象 (Terminal Object)**：任意单元素集合 $\{*\}$。
- **始对象 (Initial Object)**：空集 $\emptyset$。
- **自由函子与遗忘函子**：$\mathbf{Set}$ 是所有代数范畴（如 $\mathbf{Grp}, \mathbf{Ring}$）的底层。绝大多数代数范畴都配备一个到 $\mathbf{Set}$ 的遗忘函子 $U$（丢弃代数结构，只看底层集合）。