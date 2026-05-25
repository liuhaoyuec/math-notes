# 🧮 数学泛化定义：Embedding (嵌入映射) 的本质

> [!info] 核心认知
> Embedding 绝不仅限于 NLP（自然语言处理）。在广义数学与深度学习中，它是一个将**任意维度的离散索引张量**，映射为**高一维的连续实数张量**的标准仿射变换操作。

---

## 一、 参数定义与权重矩阵 (The Weight Matrix)

在模型内部，Embedding 层首先需要初始化并维护一个可学习的参数矩阵（即查表字典）。

* **数学语言**：
  定义一个权重矩阵 $W \in \mathbb{R}^{|V| \times d}$。
  其中，集合大小 $|V|$ 表示离散特征的总空间（即词表容量），维度 $d$ 表示被映射到的连续稠密空间的维度。矩阵的第 $i$ 行向量记作 $W_{i, :} \in \mathbb{R}^d$。

* **代码对照**：
  ```python
  # num_embeddings 对应 |V|
  # embedding_dim 对应 d
  embedding_layer = nn.Embedding(num_embeddings=|V|, embedding_dim=d)
  
  # 权重矩阵 W 可以通过 embedding_layer.weight 访问
  ```

---

## 二、 输入张量 (The Input Tensor)

* **数学语言**：
  输入张量 $X$ 可以是**任意 $k$ 维**的整数张量，形状为 $(d_1, d_2, \dots, d_k)$。
  输入张量受限于严格的定义域：张量内的任意元素 $X_{i_1, i_2, \dots, i_k} \in \mathbb{Z}$，且必须满足 $0 \le X_{i_1, i_2, \dots, i_k} < |V|$。

* **代码对照**：
  ```python
  # 输入可以是 1维 [Batch], 2维 [Batch, Seq], 甚至 3维、4维图像索引
  # 必须是 dtype=torch.long (64位整数)
  X = torch.randint(low=0, high=vocab_size, size=(d1, d2), dtype=torch.long)
  ```

---

## 三、 映射操作的数学本质 (The Mapping Operation)

将 $X$ 传入 Embedding 层，底层在数学上有两种等价的解释视角：

### 视角 1：索引寻址视角 (Lookup View)
输出张量 $Y$ 的每一个高一维向量，是通过直接“复制”矩阵 $W$ 中的特定行得到的。
$$Y_{i_1, \dots, i_k, :} = W_{X_{i_1, \dots, i_k}, :}$$

### 视角 2：独热矩阵乘法视角 (One-hot Matrix Multiplication View)
> [!tip] 最严谨的代数视角
> 深度学习框架底层为了求导，等价于将离散的 $X$ 先转换为 One-hot 张量 $X_{\text{one-hot}}$，再与权重矩阵相乘。

令函数 $O(x)$ 为将标量索引转换为长度为 $|V|$ 的 One-hot 向量的函数。
则输入张量 $X$ 经过 $O$ 变换后，变成形状为 $(d_1, d_2, \dots, d_k, |V|)$ 的张量 $X_{\text{one-hot}}$。

此时，Embedding 的操作完全等价于一个纯粹的张量点积操作：
$$Y = X_{\text{one-hot}} W$$

* **代码等价验证**：
  ```python
  # 1. 真正的 Embedding 快速操作
  Y_fast = embedding_layer(X) 
  
  # 2. 代数视角的等价操作 (极其耗费内存，但数学意义完全一致)
  X_one_hot = torch.nn.functional.one_hot(X, num_classes=vocab_size).float()
  Y_math = torch.matmul(X_one_hot, embedding_layer.weight) 
  
  # Y_fast 和 Y_math 的结果是 100% 相同的
  ```

---

## 四、 输出张量 (The Output Tensor)

* **数学语言**：
  输出张量 $Y$ 是一个在末尾增加了一维的**连续实数张量**。
  $Y \in \mathbb{R}^{d_1 \times d_2 \times \dots \times d_k \times d}$

* **代码对照**：
  ```python
  Y = embedding_layer(X)
  
  # 如果 X 的 shape 是 [B, N]
  # 那么 Y 的 shape 必然是 [B, N, d]
  print(Y.shape) 
  ```

> [!check] 总结论
> Embedding 并非什么神秘结构，它是一个**降维打击工具**。它将高维、极其稀疏、不连续的特征空间（$|V|$ 维的 One-hot 空间），通过线性矩阵乘法 $W$，强行投影到了低维、连续、可微且包含语义距离度量的空间（$d$ 维空间）中，使得微积分（梯度下降）能在符号世界里发生。