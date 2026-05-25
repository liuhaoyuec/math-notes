# 导函子与内射分解 (Derived Functors and Injective Resolutions)

> [!abstract] 核心直觉
> 在阿贝尔范畴（如模范畴或阿贝尔层范畴）中，有些操作（函子）虽然能保持序列的“单射”或“满射”性质的一部分，但会破坏完美的精确性（Exactness）。**右导函子 (Right Derived Functors) $R^i F$** 的严谨代数意义，就是用来**精确测量一个左正合函子 $F$ 破坏满射性的“误差”或“障碍”**。

## 1. 前置概念：阿贝尔范畴与足够内射 (Enough Injectives)
- **阿贝尔范畴 (Abelian Category)**：允许严谨定义核 (Kernel)、上核 (Cokernel) 和正合序列 (Exact Sequence) 的范畴。
- **内射对象 (Injective Object)**：对象 $I$ 是内射的，如果对于任何单射 $A \hookrightarrow B$，态射 $A \to I$ 总能延拓为 $B \to I$。
- **足够内射公理**：范畴中每一个对象 $M$ 都必定可以嵌入到一个内射对象 $I$ 中（即存在单射 $M \hookrightarrow I$）。

## 2. 内射分解 (Injective Resolution)
对于任意对象 $M$，通过不断将其嵌入内射对象并取商，可以构造出一个**正合的内射对象长序列**：
$$ 0 \to M \to I^0 \xrightarrow{d^0} I^1 \xrightarrow{d^1} I^2 \xrightarrow{d^2} \dots $$
其中每一个 $I^k$ 都是内射对象，且 $\text{Im}(d^{k-1}) = \ker(d^k)$。
这个序列 $I^\bullet$ 剥离了 $M$ 的复杂性，将其转化为极其“柔顺”的内射对象的链复形。

## 3. 右导函子 $R^i F$ 的严密构造
设 $F: \mathbf{A} \to \mathbf{B}$ 是一个**左正合函子 (Left Exact Functor)**。
1. **施加函子**：将函子 $F$ 作用于去除了 $M$ 的内射分解链复形：
   $$ 0 \to F(I^0) \xrightarrow{F(d^0)} F(I^1) \xrightarrow{F(d^1)} F(I^2) \to \dots $$
   *(注意：由于 $F$ 只是左正合的，这个新序列在后面可能不再正合！即 $\text{Im} \neq \ker$)*
2. **取上同调**：定义第 $i$ 个右导函子为该复形在第 $i$ 个位置的同调群：
   $$ R^i F(M) = \frac{\ker(F(d^i))}{\text{Im}(F(d^{i-1}))} $$
*(同调代数基本定理保证了：这个结果绝对独立于你选择的内射分解方式，它是 $M$ 的内蕴不变量。)*