# Vandermonde Matrix

## 1. Definition

Given scalars $ x_1, x_2, \dots, x_n \in \mathbb F$, the **Vandermonde matrix** is defined as :

$$
V(x_1,x_2,\dots,x_n)= \\
\begin{pmatrix}
1 \quad x_1 \quad x_1^2 &\quad \ldots \quad x_1^{n-1} \\
1 \quad x_2 \quad x_2^2 &\quad \ldots \quad x_2^{n-1} \\
&\vdots \\
1 \quad x_n \quad x_n^2 &\quad \ldots \quad x_n^{n-1} \\
\end{pmatrix}
$$

## 2. Determinant Formula

$$
detV(x_1,x_2,\dots,x_n) = \prod_{1 \leq i \leq j \leq n}(x_j - x_i)
$$

### Proof

The proof relies on three structural facts:

1. detV is a multivariate polynomial in $x_1,\dots,x_n$
2. if $x_i = x_j (i \neq j)$, detV = 0
3. Degree comparison determines the determinant up to a constant

#### The key lemma :Polynomial divisibility

let
$$
f(x,y, z_1, \dots, z_m) \in \mathbb F[x,y,z_1,\dots,z_m]
$$
if $f(x,y, z_1, \dots, z_m) = 0$
then (y-x) divides f.

Proof:
View f as a polynomial in y with coefficients,
By polynomial devision 
f = (y-x)q +r where r does not depend on y
$$
f(x,y,z) = (y -x)q(x,y,z) +r(x,z)
f(x,x,z) = 0 = r, r = 0
$$
substituting y = x yields r = 0, hence (y-x)|f.

Application to Vandermonde Determiant
$$
x_i = x_j\\
 detV =0,\\
 (x_j - x_i)|detV for all 1 \leq i \lt j \leq n
$$

Degree Argument

- Total degree of $\prod_{i \lt j}(x_j - x_i)$ is n(n-1)/2
- Total degree of detV is at most n(n-1)/2

therefore, 
detV = C x $\prod_{i \lt j}(x_j - x_i)$

The highest-degree monomial is 
$$
x_1^0,x_2^1,\dots,x_n^{n-1}
$$
Its coefficient is +1, hence C = 1