# MAD、CDF 与 0.67449 的关系

## 1. 结论（先记住）
- **MAD（Median Absolute Deviation）** 是一种稳健的尺度估计量
- 对正态分布，**scaled MAD ≈ 标准差 σ**
- 缩放常数 **0.6744897501960817** 来自 **标准正态分布的 75% 分位点**

---

## 2. 核心定义

### CDF（累积分布函数）
$$
F(x) = P(X \le x)
$$

### Quantile（分位数）
$$
Q(p) = F^{-1}(p) = \inf\{x: F(x) \ge p\}
$$

### MAD（未缩放）
$$
\mathrm{MAD}
= \mathrm{median}\bigl(|X - \mathrm{median}(X)|\bigr)
$$

---

## 3. 关键推导：为什么是 0.67449

设 \(Z \sim \mathcal N(0,1)\)。

中位数定义：
$$
\mathrm{median}(|Z|) = m
\quad \Longleftrightarrow \quad
P(|Z| \le m) = 0.5
$$

利用正态分布对称性：
$$
P(|Z| \le m) = P(-m \le Z \le m)
= \Phi(m) - \Phi(-m)
= 2\Phi(m) - 1
$$

解方程：
$$
2\Phi(m) - 1 = 0.5
\Rightarrow \Phi(m) = 0.75
\Rightarrow m = \Phi^{-1}(0.75)
$$

数值结果：
$$
\Phi^{-1}(0.75) \approx 0.6744897501960817
$$

---

## 4. 缩放后的 MAD（与 σ 对齐）

若 \(X \sim \mathcal N(\mu, \sigma^2)\)，则：
$$
\mathrm{median}(|X-\mu|) = \sigma \cdot 0.67448975
$$

因此定义 **scaled MAD**：
$$
\mathrm{MAD}_{\text{scaled}}
= \frac{\mathrm{median}(|X-\mathrm{median}(X)|)}{0.67448975}
\approx \sigma \quad (\text{正态下})
$$

---

## 5. 代码对应关系（Python）

```python
# 等价实现
import numpy as np

mad = np.median(np.abs(x - np.median(x))) / 0.6744897501960817

# 正态分布下 MAD 为何等于 σ · 0.67449

## 1. 结论（先记住）
若
$$
X \sim \mathcal N(\mu,\sigma^2),
$$
则
$$
\mathrm{median}\bigl(|X-\mathrm{median}(X)|\bigr)
= \sigma \cdot 0.6744897501960817.
$$

其中
$$
0.67448975 = \Phi^{-1}(0.75),
$$
是**标准正态分布的 75% 分位点**。

---

## 2. 重要前提（适用范围）
- 该等式 **仅在正态分布下严格成立**
- 在其他分布下，0.67449 只是“标定常数”，不再是精确等式

---

## 3. 第一步：标准化（位置–尺度变换）

设
$$
Z=\frac{X-\mu}{\sigma},
\quad Z\sim\mathcal N(0,1).
$$

由于正态分布对称：
$$
\mathrm{median}(X)=\mu.
$$

---

## 4. 第二步：绝对偏差的代数关系

$$
|X-\mu| = \sigma\cdot|Z|.
$$

这是**确定性的比例关系**，不是近似。

---

## 5. 第三步：中位数的尺度不变性

对任意随机变量 \(Y\) 与常数 \(a>0\)：
$$
\mathrm{median}(aY)=a\cdot\mathrm{median}(Y).
$$

因此：
$$
\mathrm{median}(|X-\mu|)
= \sigma\cdot\mathrm{median}(|Z|).
$$

---

## 6. 第四步：计算 median(|Z|)

令 \(m=\mathrm{median}(|Z|)\)，定义中位数：
$$
P(|Z|\le m)=0.5.
$$

利用正态分布的对称性：
$$
P(|Z|\le m)
= P(-m\le Z\le m)
= \Phi(m)-\Phi(-m)
= 2\Phi(m)-1.
$$

令其等于 0.5：
$$
2\Phi(m)-1=0.5
\Rightarrow \Phi(m)=0.75
\Rightarrow m=\Phi^{-1}(0.75).
$$

数值为：
$$
\Phi^{-1}(0.75)\approx 0.67448975.
$$

---

## 7. 合并结果（逻辑闭环）

$$
\begin{aligned}
\mathrm{median}(|X-\mathrm{median}(X)|)
&=\mathrm{median}(|X-\mu|) \\
&=\sigma\cdot\mathrm{median}(|Z|) \\
&=\sigma\cdot\Phi^{-1}(0.75) \\
&\approx \sigma\cdot0.67448975.
\end{aligned}
$$

---

## 8. 工程含义（为什么要除以 0.67449）

- **MAD 本身是尺度量，但与 σ 不在同一量纲**
- 除以 0.67449 后：
  $$
  \text{scaled MAD} \approx \sigma \quad (\text{正态假设下})
  $$
- 得到一个 **稳健版的标准差估计**

---

## 9. 一句话记忆锚点

> **MAD 的 0.67449 常数来自“正态分布的对称性 + 中位数定义 + 尺度不变性”，不是经验拍出来的。**

