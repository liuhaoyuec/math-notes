# 模形式核心：艾森斯坦级数 $q$-展开的绝对推导

> [!abstract] 物理意义
> 本文旨在将定义在连续几何空间（上半平面 $\mathbb{H}$）上的艾森斯坦级数 $G_k(z)$，通过解析延拓与求导算子，彻底坍缩为离散数论空间（傅里叶级数）的形态，从而引出除数函数 $\sigma_{k-1}(n)$。

---

## 一、 绝对基石：余切函数的无穷展开

在推导开始前，我们必须引入由 **米塔格-莱夫勒定理 (Mittag-Leffler Theorem)** 和 **欧拉公式 (Euler's Formula)** 共同保驾护航的绝对真理。

> [!theorem] 核心恒等式 (余切函数的 $q$ 展开)
> 设 $\tau \in \mathbb{H}$ (即 $\text{Im}(\tau) > 0$)，令 $q = e^{2\pi i \tau}$，则有绝对等式：
> $$\sum_{d=-\infty}^{\infty} \frac{1}{\tau+d} = \pi \cot(\pi \tau) = -\pi i - 2\pi i \sum_{m=1}^{\infty} q^m$$
> *(注：此处的求和定义为柯西主值对称求和 $\lim_{N \to \infty} \sum_{-N}^{N}$，底层法理由米塔格-莱夫勒的减震器 $-\frac{1}{d}$ 保证收敛，对称配对后减震器湮灭。)*

> [!note] 欧拉公式推导证明 (已证)
> $\pi \cot(\pi \tau) = \pi i \frac{e^{i\pi\tau} + e^{-i\pi\tau}}{e^{i\pi\tau} - e^{-i\pi\tau}} = \pi i \frac{q + 1}{q - 1} = -\pi i \frac{1+q}{1-q}$
> 因为 $\text{Im}(\tau) > 0$，所以 $|q| = |e^{2\pi i \tau}| < 1$。
> 动用几何级数展开：$-\pi i (1+q)(1+q+q^2+\dots) = -\pi i - 2\pi i \sum_{m=1}^{\infty} q^m$。

---

## 二、 锻造引擎：Lipschitz 公式推导

> [!proof] 疯狂求导过程
> 目标：对上述恒等式两边，关于变量 $\tau$ 连续求导 $k-1$ 次。
> 
> **1. 左边 (有理分式)：**
> 通项为 $(\tau+d)^{-1}$。
> $\frac{d}{d\tau}(\tau+d)^{-1} = -1(\tau+d)^{-2}$
> $\frac{d^2}{d\tau^2}(\tau+d)^{-1} = (-1)(-2)(\tau+d)^{-3}$
> 归纳可得，连续求导 $k-1$ 次后：
> $$\frac{d^{k-1}}{d\tau^{k-1}} \sum_{d=-\infty}^{\infty} \frac{1}{\tau+d} = \sum_{d=-\infty}^{\infty} \frac{(-1)^{k-1} (k-1)!}{(\tau+d)^k}$$
> 
> **2. 右边 (指数级数)：**
> $\frac{d}{d\tau} (-\pi i) = 0$ (常数项湮灭)。
> 对 $e^{2\pi i m \tau}$ 求导，每次根据链式法则掉下 $2\pi i m$。求导 $k-1$ 次：
> $$\frac{d^{k-1}}{d\tau^{k-1}} \left( -2\pi i \sum_{m=1}^{\infty} e^{2\pi i m \tau} \right) = -2\pi i \sum_{m=1}^{\infty} (2\pi i m)^{k-1} e^{2\pi i m \tau}$$
> 合并外围常数：$-2\pi i \cdot (2\pi i)^{k-1} = -(2\pi i)^k$。
> 
> **3. 等式缝合与符号清算：**
> 强行联立左右两边：
> $$\sum_{d=-\infty}^{\infty} \frac{(-1)^{k-1} (k-1)!}{(\tau+d)^k} = -(2\pi i)^k \sum_{m=1}^{\infty} m^{k-1} q^m$$
> **绝杀条件：** 模形式要求权重 $k$ 为**偶数**。因此 $k-1$ 为奇数，得出 $(-1)^{k-1} = -1$。
> 两边同时消去负号，并将 $(k-1)!$ 除到右边，得到终极 Lipschitz 公式！

> [!theorem] Lipschitz 公式
> 对于偶数 $k \ge 4$：
> $$\sum_{d=-\infty}^{\infty} \frac{1}{(\tau+d)^k} = \frac{(2\pi i)^k}{(k-1)!} \sum_{m=1}^{\infty} m^{k-1} q^m$$

---

## 三、 代入清算：艾森斯坦级数降维

艾森斯坦级数定义为：
$$G_k(z) = \sum_{(c,d) \in \mathbb{Z}^2 \setminus \{(0,0)\}} \frac{1}{(cz+d)^k}$$

> [!proof] 网格切割与代入
> 我们将二维网格切分为 $c = 0$ 和 $c \neq 0$ 两部分。
> 
> **1. 处理 $c = 0$ 轴：**
> $$ \sum_{d \neq 0} \frac{1}{d^k} = \sum_{d=1}^{\infty} \frac{1}{d^k} + \sum_{d=-\infty}^{-1} \frac{1}{d^k} $$
> 因为 $k$ 是偶数，正负对称，所以该式精确等于 $2\sum_{d=1}^{\infty} \frac{1}{d^k}$。
> *(注：此即黎曼 Zeta 函数的绝对定义：$\zeta(k) = \sum_{n=1}^{\infty} \frac{1}{n^k}$)*
> 故 $c=0$ 部分贡献了：$2\zeta(k)$。
> 
> **2. 处理 $c \neq 0$ 平原：**
> 利用中心对称性 $(-c, -d) \to (c, d)$ 以及偶数次幂 $(-1)^k = 1$，将 $c \in \mathbb{Z} \setminus \{0\}$ 折叠为只计算 $c > 0$ 的部分，然后整体乘以 2：
> $$ 2 \sum_{c=1}^{\infty} \sum_{d=-\infty}^{\infty} \frac{1}{(cz+d)^k} $$
> **3. 降维打击：** > 令 $\tau = cz$，直接将第一步锻造的 Lipschitz 公式代入内层求和：
> $$ 2 \sum_{c=1}^{\infty} \left[ \frac{(2\pi i)^k}{(k-1)!} \sum_{m=1}^{\infty} m^{k-1} e^{2\pi i m (cz)} \right] $$

---

## 四、 终极聚合：数论神迹降临

提取外围常数后，我们面对的是双重无穷求和：
$$\frac{2(2\pi i)^k}{(k-1)!} \sum_{c=1}^{\infty} \sum_{m=1}^{\infty} m^{k-1} q^{mc}$$

> [!proof] 合并同类项与除数函数
> 令新变量 $n = mc$（$n$ 显然遍历所有正整数 $1, 2, 3 \dots$）。
> 我们不再分别对 $c$ 和 $m$ 求和，而是按照 $q^n$ 的项数进行**重排**。
> 对于每一个固定的 $n$，其对应系数为满足 $m \cdot c = n$ 的所有 $m^{k-1}$ 的加和。
> 满足条件的 $m$ 即为 $n$ 的正约数（记作 $m \mid n$）。
> 
> 引出数论核心函数：**除数函数 $\sigma_{k-1}(n)$**
> $$\sigma_{k-1}(n) = \sum_{m \mid n} m^{k-1}$$
> 
> 将双重求和坍缩为一重求和：
> $$\sum_{n=1}^{\infty} \left( \sum_{m \mid n} m^{k-1} \right) q^n = \sum_{n=1}^{\infty} \sigma_{k-1}(n) q^n$$

> [!theorem] 艾森斯坦级数傅里叶展开式 (终极形态)
> $$G_k(z) = 2\zeta(k) + \frac{2(2\pi i)^k}{(k-1)!} \sum_{n=1}^{\infty} \sigma_{k-1}(n) q^n$$
> *(这标志着连续几何分析正式向离散数论交出最高统治权)*