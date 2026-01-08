# Jordan 块

## 泛特征向量不变空间

## 其他非泛特征向量空间

$$
p(x) = x^2 -2ax +(a^2+b^2),b \neq 0 \\
p(x) = (x - (a+bi))(x - (a-bi))
$$
在实空间中，对应的不变子空间是：$W_{a,b} = ker(T^2 -2aT + (a^2+b^2)I)^k

- a:控制缩放/衰减
- b:控制旋转角速度

对任意向量$v \in W_{a,b}$:,T作用一次先缩放$sqrt{a^2+b^2}$,再旋转角度$arg(a+bi)$


## T在泛特征向量空间的行为

$G(\lambda,T)$ 是特征值 $\lambda$ 的泛特征向量不变子空间,即 $ker((T-\lambda I)^k, k \leq dim(G)) $;

- $k \leq dim(G)$ 是因为每次作用$T-\lambda I$一次，最少消去一个新的维度，此时只有一条Jordan 链 $v_3 \to v_2 \to v_1 \to 0 $
- 也可以多条Jordan链，并行塌缩

$$
v_3 \xrightarrow{T-\lambda I} v_2 \xrightarrow{T-\lambda I} v_1 \xrightarrow{T-\lambda I} 0 \\
w_3 \xrightarrow{T-\lambda I} w_2 \xrightarrow{T-\lambda I} w_1 \xrightarrow{T-\lambda I} 0
$$

- $dim(ker(T- \lambda I)^j) - dim(ker(T-\lambda I)^{j-1}) =$ 长度$\geq j$的Jordan 链的条数
- k 只取决于最大Jordan链的长度，也就是max{Jordan块的大小}

$T ｜_G= \lambda I + N |_G$， $N = T - \lambda I $是dim(G) 上的幂零算子，即$N^k｜_G = 0$

- $T^n$ 的展开

$$
T^n = \sum_{j=0}^{k-1} \binom{n}{j} \lambda^{n-j}N^j \\
T^nv_k = \lambda^nv_k + n\lambda^{n-1}v_{k-1}+ \dots+ \binom{n}{k-1}\lambda^{n-k+1}v_1
$$

- 幂零算子在G 泛特征向量空间的行为:$v = a_1v_1 + a_2v_2+ a_3v_3$, 假定dimG =3， 为单链$v_i为泛特征向量基链。

$$
v_3 \xrightarrow{N} v_2 \xrightarrow{N} v_1 \xrightarrow{N} 0 \\
$$
$Nv$作用一次，$v_3$分量 $ \to v_2$ ;$v_2$分量 $ \to v_1$ ;$v_1$分量 $ \to 0$;

- 因为$N^kv_k = 0$,$v_1$是T在$\lambda$的特征向量，第k之后不会再出现$v_0,v_{-1}$ 之类的新方向，所有分量已经全部“落”在$span\{v_1,\dots,v_k\}$
- 几何上表现为：向量越来越贴近特征向量方向，但不再改变方向集
- 第一次T，立方体整体缩放$\lambda$,Jordan剪切一次，产生新方向；多次之后，立方体变成极度扁长的平行六面体，最长轴方向为特征向量方向；其他方向仍然存在,$dimimgT^n = dimG (\lambda \neq 0;$，但几何上被压制
- $\lambda =0$时T = N，因此T 的每一次作用都会沿 Jordan 链方向把向量向下推进，并导致 image 空间的维数逐步减少，最终塌陷到{0}

## 从上三角到Jordan型

在某个固定 $\lambda$ 的块上 
$$
A_\lambda = \lambda I +U
$$
其中U是幂零，因此其唯一特征值为0；

- 任何幂零线形算子都存在一组基，使得它的矩阵是若干Jordan块（对角为0，上超对角为1），因为通过Jordan链，从kerU 向上拉出链

$$
Uv_1 = 0, Uv_2 = v_1, Uv_3 = v_2,/dots
$$
于是矩阵就变成：
$$
J_\lambda =
\begin{pmatrix}
\lambda \quad 1 \quad 0 \quad & \dots \\
0 \quad \lambda \quad 1 \quad & \dots \\
0 \quad 0 \quad \lambda \quad & \dots \\
\vdots  & \ddots \\

\end{pmatrix}
$$
