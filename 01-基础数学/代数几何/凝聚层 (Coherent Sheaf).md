# 凝聚层 (Coherent Sheaf)

> [!abstract] 严谨定义
> $X$ 上的一个 $\mathcal{O}_X$-模层 $\mathcal{F}$ 是**凝聚的 (Coherent)**，必须同时满足以下三个极其严苛的代数条件：
> 1. $\mathcal{F}$ 是 [[拟凝聚层 (Quasi-coherent Sheaf)]]。
> 2. **有限型 (Finite Type)**：$\mathcal{F}$ 在局部上是由**有限个**生成元生成的（即表现序列中的指标集 $I$ 是有限集）。
> 3. **有限表现 (Finite Presentation) 闭包**：对于任意开集 $U$ 以及任意的层同态 $\phi: \mathcal{O}_U^n \to \mathcal{F}|_U$，其**核 (Kernel, 即生成元之间的关系层)** 必须也是有限型的。

## 1. 诺特概形上的终极化简
上述第三条定义极其繁琐（为了处理非诺特情况）。但在代数几何的实际研究中，绝大多数空间是 [[诺特概形 (Noetherian Scheme)]]。
**塞尔定理 (Serre's Theorem)**：如果 $X$ 是局部诺特概形，那么 $\mathcal{F}$ 是凝聚层 **当且仅当** $\mathcal{F}$ 是拟凝聚层，且局部有限生成。
- **代数对应**：在仿射开集 $\text{Spec}(A)$ 上（$A$ 为诺特环），$\mathcal{F} \cong \tilde{M}$，且 $M$ 是一个**有限生成的 $A$-模**。

## 2. 凝聚层的“奇迹”性质 (阿贝尔范畴)
凝聚层拥有极度完美的代数性质：
- 任意两个凝聚层之间的态射的 **核 (Kernel)**、**上核 (Coker)**、**像 (Image)** 依然绝对是凝聚层。
- 凝聚层构成了 $\mathcal{O}_X$-模范畴中的一个**厚阿贝尔子范畴 (Thick Abelian Subcategory)**。这意味着所有同调代数（导函子、Ext、Tor）在凝聚层中运算都不会“逃逸”。

## 3. 几何意义 (有限维的保证)
凝聚层在概形论中充当了“有限维向量空间”的推广。
**凝聚层上同调的有限性定理 (Finiteness Theorem)**：如果 $X$ 是某个诺特环上的 [[真态射 (Proper Morphism)]] 定义的概形，那么对于任意凝聚层 $\mathcal{F}$，其层上同调群 $H^i(X, \mathcal{F})$ **必然是有限生成的模（即有限维向量空间）**。
（我们在之前推导椭圆曲线 $l(nO)=n$ 的维度计算时，其底层依据正是凝聚层上同调的有限性！）