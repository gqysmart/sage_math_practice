# Rayleigh Quotient Problem

## Problem Description

Given a real symmetric matrix
$$
A \in \mathbb R^{n \times n}, A = A^T
$$
consider the quadratic form
$$
q(v) = v^TAv, v \in \mathbb R^n 
$$
The problem concerns the **directional behavior** of this quadratic form. Rath than studying how $q(v)$ scales with the magnitude of v,we are interesting in how it varies **across different directions**.

The central question is :

```text
Along which directions does the quadratic form induced by A attain its extreme values?
```

---

## Objective

The objective is to find unit-norm vectors that maximize(minimize) the quadratic form:
$$
\max_{||v=1||}v^TAv
$$

Equivalently, the objective can be stated as maximizing the **Rayleigh quotient**

$$
\max_{v \neq 0} R(v) = \frac{v^TAv}{v^Tv}
$$

---

## Assumptions

### Matrix Assumptions

- A is a real symmetric matrix
- As a consequence, A admits an orthogonal eigen-decomposition.

### Space Assumptions

- The vector space is the finite-dimensitional Euclidean space $ \mathbb R^n$
- The inner product is the standard Euclidean inner product:

$$
\langle u,v \rangle = u^Tv
$$

### Feasiblity Assumptions

- The constraint set $ \{ v \in \mathbb R^n:||v||=1 \} $ is compact.
- The quadratic form is continuous on this set, so extrema are guaranteed to exist.

## Model

### Optimization Model

The Rayleigh Quotient problem is formulated as a constrained optimization problem:
$$
\text{maximize} \quad v^TAv \\
\text{subject to} \quad v^Tv = 1
$$

### Variational Formulationn

Due to the homogeneity of the quadratic form, the constrained problem is equivalent to the unconstrained variational problem:

$$
\max_{v \neq 0} R(v) = \frac{v^TAv}{v^Tv}
$$
This formulation emphasize that the problem is **Scale-invariant** and depends only on direction.

### Structural Consequence(Model-Level Result)

Under the stated assumptions, any extremizer v of the Rayleigh quotient satifies the stationary conditon:
$$
Av = \lambda v
$$
for some scalar $\lambda$.
Thus,:

- Extreme values of the Rayleigh quotient are eigenvalues of A
- Extreme directions are the corresponding eigenvectors(normalized).
This is a property of the model, independent of any numerical algorithm.

## Theory/Model Properties

### Rayleigh-Ritz Theorem

#### Proof

##### Step 1:

Introduce the constraint $g(v) =v^top v- 1 = 0$ and the Lagrangian 
$$
\mathcal{L}(v,\lambda) = v^\top A v -\lambda(v^\top v -1)
$$

Because $A$ is symmetric, the gradient satisfies

$$
df = (dv)^T A v + v^T A dv \\
$$
$v^T A dv$ 是标量，所以 $s^T = s$

$$
df = (dv)^T A v + (dv)^T A^T v = (dv)^T (A+A^T) v \\
\nabla_v (v^\top A v) = 2Av,
\qquad
\nabla_v (v^\top v)=2v.
$$
At a stationary point $(v,\lambda)$
$$
\nabla_v \mathcal{L}(v,\lambda) =0 \;\Longrightarrow \;2Av -2\lambda v =0 \; \Longrightarrow \;Av = \lambda v
$$
Thus, every constrained stationary point $v$ is an eigenvector of $A$. since $||v|| = 1$
$$
f(v)=v^\top A v = v^\top (\lambda v)=\lambda (v^\top v)=\lambda.
$$
So the objective value at a stationary point equals the corresponding eigenvalue.

#### Step 2:The maximum value is the largest eigenvalue

By the spectral theorem, there exists an orthogonal matrix $Q$ and a diagonal matrix

$$

\Lambda=\mathrm{diag}(\lambda_1,\dots,\lambda_n),
\quad \lambda_1\ge \lambda_2\ge \cdots \ge \lambda_n,
$$
such that,
$$
A = Q \Lambda Q^\top.
$$
Take any unit vector $v$ with $\|v\|=1$ and set $y = Q^\top v$. Since $Q$ is orthogonal,
$$
\|y\|=\|v\|=1
\quad\Longrightarrow\quad
\sum_{i=1}^n y_i^2 = 1.
$$
Then
$$
v^\top A v
= v^\top Q \Lambda Q^\top v
= y^\top \Lambda y
= \sum_{i=1}^n \lambda_i y_i^2.
$$
Because $y_i^2 \ge 0$ and $\sum_i y_i^2 = 1$, the expression $\sum_i \lambda_i y_i^2$ is a convex combination of the eigenvalues. Hence,
$$
v^\top A v
= \sum_{i=1}^n \lambda_i y_i^2
\le \lambda_1 \sum_{i=1}^n y_i^2
= \lambda_1
= \lambda_{\max}(A).
$$
This upper bound is attainable by choosing $y=e_1=(1,0,\dots,0)$, which corresponds to $v=Qe_1$, the eigenvector associated with $\lambda_1$. Therefore,
$$
\max_{\|v\|=1} v^\top A v = \lambda_{\max}(A),
$$
and the maximizers are exactly the unit vectors in the eigenspace of $\lambda_{\max}(A)$.

### Extension: the 2nd, 3rd, ... directions (Courant–Fischer / successive Rayleigh–Ritz)

Let $A \in \mathbb{R}^{n\times n}$ be symmetric with eigenvalues
$$
\lambda_1 \ge \lambda_2 \ge \cdots \ge \lambda_n,
$$
and corresponding orthonormal eigenvectors $q_1,\dots,q_n$.

#### Successive constrained maximization (PCA-style formulation)

Define $v_1,\dots,v_k$ recursively by:
$$
v_1 \in \arg\max_{\|v\|=1} v^\top A v,
$$
and for $j\ge 2$,
$$
v_j \in \arg\max_{\|v\|=1,\; v \perp v_1,\dots,v_{j-1}} v^\top A v.
$$

Then:

- The optimal value at step $j$ equals $\lambda_j$.
- Any maximizer $v_j$ is a unit vector in the eigenspace associated with $\lambda_j$.
- If $\lambda_j$ has multiplicity $>1$, the maximizer is not unique: any unit vector in that eigenspace (also orthogonal to the previously chosen vectors) is valid.

In particular, one valid choice is:
$$
v_j = q_j, \quad j=1,\dots,k,
$$
so that
$$
v_j^\top A v_j = \lambda_j.
$$
---

#### Why this works (short proof sketch)

Using the spectral decomposition $A=Q\Lambda Q^\top$, write any unit vector $v$ as
$$
v = \sum_{i=1}^n y_i q_i, \quad \sum_{i=1}^n y_i^2 = 1,
$$
so
$$
v^\top A v = \sum_{i=1}^n \lambda_i y_i^2.
$$

The orthogonality constraints $v \perp q_1,\dots,q_{j-1}$ force
$$
y_1=\cdots=y_{j-1}=0.
$$
Therefore,
$$
v^\top A v = \sum_{i=j}^n \lambda_i y_i^2 \le \lambda_j \sum_{i=j}^n y_i^2 = \lambda_j,
$$
and equality is achieved by choosing $v=q_j$ (or any unit vector in the $\lambda_j$-eigenspace).

---

#### Courant–Fischer min–max form (reference statement)

For symmetric $A$,
$$
\lambda_k
=
\max_{\dim(S)=k}\;\min_{\substack{v\in S\\ \|v\|=1}} v^\top A v
=
\min_{\dim(S)=n-k+1}\;\max_{\substack{v\in S\\ \|v\|=1}} v^\top A v.
$$

This gives a complete variational characterization of $\lambda_1,\lambda_2,\dots,\lambda_n$.






