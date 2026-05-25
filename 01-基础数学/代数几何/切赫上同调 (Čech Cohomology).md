# 切赫上同调 (Čech Cohomology)



> [!abstract] 核心直觉
> 导函子的内射分解虽然在理论上无懈可击，但在实际中**极度难以计算**（内射层太过庞大）。
> **切赫上同调 $\check{H}^i(\mathcal{U}, \mathcal{F})$** 是一种依赖于具体开覆盖 $\mathcal{U}$ 的计算方法。它通过交集上的“组合差值”来显式构造复形。在良好的条件下，它与抽象的导函子上同调严格同构。

## 1. 严密构造过程
设 $\mathcal{U} = \{U_i\}_{i \in I}$ 是 $X$ 的一个开覆盖（设指标集 $I$ 全序）。设 $\mathcal{F}$ 为阿贝尔层。
1. **切赫上链 (Čech Cochains)**：定义第 $p$ 阶切赫复形为所有 $p+1$ 重交集上截面的直积：
   $$ \check{C}^p(\mathcal{U}, \mathcal{F}) = \prod_{i_0 < i_1 < \dots < i_p} \mathcal{F}(U_{i_0} \cap U_{i_1} \cap \dots \cap U_{i_p}) $$
   *(例如：$\check{C}^0$ 是各开集上的截面族，$\check{C}^1$ 是两两交集上的截面族。)*
2. **边缘同态 (Boundary Map)**：定义 $d^p: \check{C}^p \to \check{C}^{p+1}$，通过交替符号取限制差值：
   $$ (d^p s)_{i_0 \dots i_{p+1}} = \sum_{k=0}^{p+1} (-1)^k s_{i_0 \dots \hat{i_k} \dots i_{p+1}}|_{U_{i_0 \dots i_{p+1}}} $$
   *(注：$\hat{i_k}$ 表示略去该指标。容易验证 $d^{p+1} \circ d^p = 0$。)*
3. **取同调**：$\check{H}^p(\mathcal{U}, \mathcal{F}) = \frac{\ker(d^p)}{\text{Im}(d^{p-1})}$。

## 2. 塞尔定理 (Serre's Theorem on Čech Cohomology)
在什么时候切赫上同调等于真正的层上同调？
**定理**：设 $X$ 是一个 [[分离概形 (Separated Scheme)]]，$\mathcal{U}$ 是 $X$ 的一个**仿射开覆盖**。如果 $\mathcal{F}$ 是一个 [[拟凝聚层 (Quasi-coherent Sheaf)]]，那么对于所有的 $i \ge 0$：
$$ \check{H}^i(\mathcal{U}, \mathcal{F}) \cong H^i(X, \mathcal{F}) $$
**意义**：分离性保证了仿射开集的交集依然是仿射的；拟凝聚层在仿射概形上的高阶上同调严密为 0（Cartan 定理 B）。这使得开覆盖 $\mathcal{U}$ 成为了计算上同调的完美“无环覆盖 (Acyclic Cover)”。我们终于可以把抽象同调转化为有限维矩阵的线性代数运算！