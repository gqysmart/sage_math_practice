# PCA - Principal Component Analysis

## 1. Problem

### 1.1 Problem Statement

Given a set of high-dimensional data samples:
$$
x_1, x_2, \ldots, x_n \in \mathbb{R}^d
$$

the goal is to represent the data in a lower-dimensional subspace ($k \ll d$) while preserving as much relevant information as possible.

---

### 1.2 Objective

- Find a set of orthogonal directions $v_1,v_2, \ldots, v_k$
- Such that the sample variance(a statistic) of the data projected onto these directions is maximized

$$
\max_{v} S^2(v)= \frac{1}{n}\sum_{i=1}^{n} \bigl( v^\top X_i - v^\top\bar{X} \bigr)^2

$$

- Use a small number of dimensions to capture the dominant structure of the data

---

### 1.3 Assumptions

- The data has been centered(zero mean)
- Only linear structure is considered
- Information is measured using second-order statistics (variance/ covariance)

---

## 2. Model

This problem is formulated using the following modeling abstractions:

- **Covaiance Model**

The global structure of the data is described by second-order statistics

- **Quadratic Form Model**

Projected variance can be expressed as a quadratic form optimaztion problem.

See model definition in:

- [M-001_Covariance.md](../models/M_001_Covariance.md)
- [M_002_Quadratic_Form.md](../models//M_002_Quadratic_Form.md)

## Notes

1. PCA 问题，

$$
arg(v) \max_{||v|| = 1} Var(v^TX) \iff arg(v) \max_{||v||=1}v^T \Sigma v
$$

$ v^T X$表示随机向量X在v方向的投影, 其是一个随机变量； $\Sigma$为协方差算子
$$
Cov(X) = \mathbb E (XX^T) =\Sigma
$$

证明：令随机变量$Y = v^TX$,v(nx1)为常量,X(nx1)随机变量; $v^TX = X^Tv =标量$
$$
\mathbb{E} (Y) = E(v^T X) = v^T \mathbb{E}X = v^t \mu \\ 
\begin{aligned}
Var(Y) &= \mathbb{E}([Y-E(Y)^2]) \\
&= \mathbb{E}(v^TX-v^T\mu)^2 \\
&= \mathbb{E}(v^T(X - \mu))(v^T(X - \mu)) \\
&= \mathbb{E}(v^T(X - \mu)(X-\mu)^Tv) \\
&= v^T \Sigma v
\end{aligned} \\
$$
By the Rayleigh-Ritz theorem, the solution is given by the leading eigenvectors of $\Sigma$.

See: [P_002_Rayleigh_Quotient.md](./P_002_Rayleigh_Quotient.md)

1. PCA can be computed via SVD because the covariance matrix satisfies
Σ = (1/n) XᵀX. The eigenvectors of Σ are therefore identical to the right
singular vectors of X, and the eigenvalues correspond to the squared
singular values scaled by 1/n. Hence, performing SVD on the centered data
matrix directly yields the principal components without explicitly forming the covariance matrix.


