# 仿射无关 (Affine Independence) 的多维等价定义与互推

在代数几何与计算拓扑中，“仿射无关”用于描述一组点能够“撑起最高维度空间”而不发生坍缩的几何属性。给定 $\mathbb{R}^n$ 空间中的 $k+1$ 个点：$V = \{v_0, v_1, \dots, v_k\}$。

## 1. 等价定义体系

> [!info] 定义一：位移向量的线性无关（几何视角）
> 任选其中一点（如 $v_0$）作为局部原点，构造 $k$ 个位移向量 $u_i = v_i - v_0$（其中 $i = 1, 2, \dots, k$）。
> 如果这 $k$ 个向量在 $\mathbb{R}^n$ 中是**线性无关**的，则称集合 $V$ 仿射无关。

> [!abstract] 定义二：零和仿射组合的唯一性（代数对称视角）
> 考虑这 $k+1$ 个点的线性组合方程：
> $$\sum_{i=0}^k \lambda_i v_i = \mathbf{0}$$
> 并且附加一个**系数和为零**的超平面约束：
> $$\sum_{i=0}^k \lambda_i = 0$$
> 如果满足上述两个方程的**唯一解**是 $\lambda_0 = \lambda_1 = \dots = \lambda_k = 0$，则称集合 $V$ 仿射无关。

> [!example] 定义三：矩阵满秩判据（计算视角）
> 有两种等价的矩阵构造形式来判定：
> 1. **位移矩阵法：** 构造 $k \times n$ 矩阵 $\mathbf{D}$，其第 $i$ 行为 $v_i - v_0$。集合 $V$ 仿射无关 $\iff \text{Rank}(\mathbf{D}) = k$。
> 2. **增广矩阵法：** 构造 $(k+1) \times (n+1)$ 矩阵 $\mathbf{M}$，将所有点写成行向量，并在末尾追加一列 $1$。集合 $V$ 仿射无关 $\iff \text{Rank}(\mathbf{M}) = k+1$。

---

## 2. 核心互推证明 (Def 1 $\iff$ Def 2)

这个互推完美展示了如何将“带有特殊原点”的几何概念，转化为“平移不变”的对称代数系统。

> [!check] 证明：定义一 $\implies$ 定义二
> **已知：** 向量组 $\{v_1 - v_0, \dots, v_k - v_0\}$ 线性无关。
> **假设存在** 一组系数 $\lambda_0, \dots, \lambda_k$ 满足 $\sum_{i=0}^k \lambda_i v_i = \mathbf{0}$ 且 $\sum_{i=0}^k \lambda_i = 0$。
> 由约束可知 $\lambda_0 = -\sum_{i=1}^k \lambda_i$。代入第一个方程：
> $$-\left(\sum_{i=1}^k \lambda_i\right) v_0 + \sum_{i=1}^k \lambda_i v_i = \mathbf{0}$$
> 合并同类项：
> $$\sum_{i=1}^k \lambda_i (v_i - v_0) = \mathbf{0}$$
> 因为已知位移向量线性无关，故必定有 $\lambda_1 = \lambda_2 = \dots = \lambda_k = 0$。
> 再代回约束条件 $\lambda_0 = -\sum_{i=1}^k \lambda_i$，得 $\lambda_0 = 0$。
> **证毕：** 所有系数必定全为 $0$。

> [!check] 证明：定义二 $\implies$ 定义一
> **已知：** $\sum_{i=0}^k \lambda_i v_i = \mathbf{0}$ 且 $\sum_{i=0}^k \lambda_i = 0$ 只有零解。
> **假设存在** 一组系数 $\mu_1, \dots, \mu_k$ 使得位移向量的线性组合为零：
> $$\sum_{i=1}^k \mu_i (v_i - v_0) = \mathbf{0}$$
> 展开并整理：
> $$\sum_{i=1}^k \mu_i v_i - \left(\sum_{i=1}^k \mu_i\right) v_0 = \mathbf{0}$$
> 此时，我们人为构造一组新的系数 $\lambda$：
> 令 $\lambda_i = \mu_i$ (对 $i=1,\dots,k$)，令 $\lambda_0 = -\sum_{i=1}^k \mu_i$。
> 则显然有 $\sum_{i=0}^k \lambda_i v_i = \mathbf{0}$，且这组系数之和 $\sum_{i=0}^k \lambda_i = \lambda_0 + \sum_{i=1}^k \mu_i = 0$。
> 根据已知条件（全零解），必定有 $\lambda_i = 0$。
> 故 $\mu_1 = \mu_2 = \dots = \mu_k = 0$。
> **证毕：** 位移向量必然线性无关。