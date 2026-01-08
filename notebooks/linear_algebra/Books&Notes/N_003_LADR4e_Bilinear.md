# 双线形

$$
\varphi \in V^*, \varphi: V \mapsto \mathbb{F}
$$
在内积空间，由Riesz定理:每个线形泛函表示在v方向的内积测量$V^*$对偶空间 向量与V空间向量，1-1对应.
存在唯一$v \in V$

$$
\varphi(v)(u) = \langle u,v \rangle \quad \forall u \in V \\
$$
$
\varphi_v(u) = \langle u,v \rangle
$
表示u在v方向的内积测量，$v \mapsto \varphi_v \in V^*$

## 从线形泛函到双线形

双线形
$$
\beta: V \times V \to \mathbb{F}
$$
双线形形式可以理解为“给每个向量v，分配一个线形泛函$ \beta(\cdot, v)$; 对于内积空间，表示对输入向量u，在某个与v相关的方向的内积测量。
$$
\Phi :V \to V^* \\
\beta(u,v) \coloneqq \Phi(v)(u)
$$
($\coloneqq$表示定义为)

***双线形$\beta \iff$ 线形映射 $\Phi :V \to V^* $***，
$$

V^* \cong V \\
\Phi: V \to V^* \iff T:V \to V, \\
$$
对内积空间，Risez定理知道该与v相关的泛函 对应与向量w(v)的内积 即 
$$
\Phi(v)(u) = \langle u, w(v) \rangle \\
\beta(u,v) = <u,Tv>
$$
v经过一个变换T后，作为测量方向，去测量u。

## $\beta$的矩阵形式和T的矩阵形式

$V$是有限维内积空间，选定一组基$ {e_1, \dots, e_n}$(不一定正交)， 内积在该基下的Gram矩阵为
$$
G_{ij} = \langle e_i,e_j \rangle
$$

### $\beta$的矩阵形式

在基$\{ e_i\}$下，定义矩阵：
$$
B_{ij} = \beta(e_i,e_j), \\
u = \sum_i u_ie_i, v = \sum_j v_je_j \\
\beta(u,v) = u^\top Bv
$$

### T的矩阵形式

设T在同一组基下的矩阵为A，$\beta(u,v) = <u,Av>$,而内积在坐标层面是：
$$
<u,w> = u^\top Gw \\
\beta(u,v) = u^\top GAv \\
$$
所以对任意u,v成立，
$$
u^\top Bv \quad vs \quad u^\top GAv \Rightarrow \\
B = GA ; A = G^{-1}B
$$
对于正交归一基，$G = I \Rightarrow B = A$;在非正交基下，双线形的矩阵 B 与算子的矩阵  一般不同，
它们通过内积的 Gram 矩阵 𝐺关联。
