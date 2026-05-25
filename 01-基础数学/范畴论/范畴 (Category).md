# 范畴 (Category)

> [!abstract] 严谨定义
> 一个**范畴** $\mathcal{C}$ 是由以下数据和公理构成的数学结构：
> 1. **对象类 (Class of Objects)**：记作 $\text{Ob}(\mathcal{C})$。
> 2. **态射集 (Morphisms/Arrows)**：对于任意两个对象 $X, Y \in \text{Ob}(\mathcal{C})$，存在一个态射集合 $\text{Hom}_{\mathcal{C}}(X, Y)$（或记作 $\mathcal{C}(X, Y)$）。若 $f \in \text{Hom}_{\mathcal{C}}(X, Y)$，记作 $f: X \to Y$。
> 3. **复合运算 (Composition)**：对于任意对象 $X, Y, Z$，存在一个映射 $\circ: \text{Hom}_{\mathcal{C}}(Y, Z) \times \text{Hom}_{\mathcal{C}}(X, Y) \to \text{Hom}_{\mathcal{C}}(X, Z)$，记作 $(g, f) \mapsto g \circ f$。

## 公理系统
范畴必须绝对满足以下两条公理：
1. **结合律 (Associativity)**：对于任意态射 $f: X \to Y, g: Y \to Z, h: Z \to W$，恒有 $h \circ (g \circ f) = (h \circ g) \circ f$。
2. **单位元存在性 (Identity)**：对于任意对象 $X$，存在唯一的恒等态射 $\text{id}_X \in \text{Hom}_{\mathcal{C}}(X, X)$，使得对任意 $f: X \to Y$ 和 $g: Z \to X$，恒有 $f \circ \text{id}_X = f$ 且 $\text{id}_X \circ g = g$。

> [!info] 局部小范畴 (Locally Small Category)
> 如果对于任意 $X, Y$，$\text{Hom}_{\mathcal{C}}(X, Y)$ 都是一个**集合 (Set)**（而不是真类 Proper Class），则称该范畴为局部小的。我们日常研究的绝大多数范畴（除了范畴的范畴等极端情况）都是局部小范畴。