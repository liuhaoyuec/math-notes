# 🧠 05 范畴化深度学习 — Categorical Deep Learning

> 📎 打通 **第3阶范畴论** ↔ **第5阶AI数学** 的桥梁

本目录包含范畴化深度学习的核心文献与教程，源自ICML 2024论文：
**"Categorical Deep Learning: An Algebraic Theory of All Architectures"**
(Bruno Gavranović, Paul Lessard, Andrew Dudzik et al., Google DeepMind & Symbolica AI)

---

## 🎯 为什么这很重要？

这可能是目前**最激进的"数学统一深度学习"尝试**——用范畴论中的单子（Monad）、自函子代数/余代数、Para 2-范畴，统一刻画：

| 概念 | 传统视角 | 范畴化统一视角 |
|------|---------|--------------|
| 等变层（CNN等） | GDL→群表示论 | **群作用单子的代数同态** |
| 循环网络（RNN） | 手写展开公式 | **列表自函子的自由单子代数** |
| 递归网络（TreeRNN） | 树结构的递归定义 | **二叉树自函子的始代数+fold** |
| 自动机（Mealy/Moore） | 状态机 | **自函子余代数+unfold** |
| 权重共享（Weight Tying） | 工程trick | **Para 2-范畴中lax代数的余幺半群结构** |

---

## 📂 文件

| 文件 | 说明 |
|------|------|
| `深度学习与范畴.pdf` | ICML 2024 原始论文 (39页) |
| `范畴深度学习完整教程.pdf` | 中文教程：逐节翻译+严谨补充+交换图 (22章) |

---

## 🔗 体系位置

```
第3阶 范畴论 ──────┐
                    ├──→ 05 范畴化深度学习 ──→ 第5阶 AI的数学
第5阶 AI的数学 ────┘
```

- **前置知识**：理解单子、自函子、代数/余代数（见 03-范畴论）
- **向下连接**：神经网络的具体实现（见 06-工程数学 & 05-AI的数学）
- **向上连接**：更一般的代数几何与层论中的单子（见 04-代数几何·概形论）

---

## 📖 核心数学框架速览

### 群等变性 = 群作用单子的代数同态

$$\text{Geometric DL} \iff \text{Monad Algebra Homomorphism of } G \times -$$

$$
\begin{CD}
G \times X @>{G\times f}>> G \times Y \\
@V{\alpha}VV @VV{\beta}V \\
X @>>{f}> Y
\end{CD}
\quad\Longrightarrow\quad f(g \cdot x) = g \cdot f(x)
$$

### 列表/树 = 自函子 $1 + A \times -$ 的始代数

$$\text{RNN} \iff \text{Free Monad on } 1 + A \times - \text{ in } \mathbf{Para}$$

### 权重共享 = Lax代数产生的余幺半群

$$\Delta_P : P \to P \otimes P \quad\text{(复制参数)}$$
$$!_P : P \to I \quad\text{(删除参数)}$$

---

*"范畴深度学习是：所有架构的代数理论"*