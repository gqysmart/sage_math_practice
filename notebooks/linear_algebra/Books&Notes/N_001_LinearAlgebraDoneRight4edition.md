# Note for "Linear algebra done right v4"

The book link：[Linear algebra done right v4](./B_001_LinearAlgebraDoneRight4edition.pdf)

## OVERVIEW

- 线形结构关系 = 生成关系+依赖关系+可保持性
线形结构关系是指向量之间由加法和数乘所决定的线形生成与依赖关系，而线形变换正是保持这种结构的映射。
- 基的作用，不是构成空间，而是“线形结构的一个最小坐标化接口”：
任意向量 $ v=a_1e_1+a_2e_2+\ldots+a_ne_n $ ,这种表示是唯一的，让关系可以被编码成坐标、矩阵，从而可以代数运算。
- 由于线形变换在抽象层，有语义但不直观也不可计算，通过选择不同的基，将线形变换转换为矩阵，从而将几何或结构性的操作转换为符合人类或计算机认知和计算习惯的代数运算， 从而显示地揭示其不变量，分类特征，同时引入表示层面相关的附加性质，从而使得分析和计算成为可能。
  - 线形变换的不变量与基的选择无关，
    - 结构级：kernal(T),image(T),是否可逆，
    - 等价类：谱(特征值集合)，特征多项式，Jordan结构，(等价类 = 在选定的“忽略规则”下，代表同一个抽象对象的所有具体实现的集合)
    - 标量：det(T),Trace(T)
    - 内积空间的不变量：奇异值，||T||,
  - 矩阵引入了新的表示层面的结构：稀疏性，上三角， 数值稳定性， 条件数， 计算复杂度等

## 向量空间

- 数学不是从“有意义的对象”到“无意义的形式”， 而是从“最少可区分关系”出发，逐步引入更多结构，从而增加“可区分数学关系”
  - 集合 代表了最弱的结构，结构语义上提供了 相等和不相等
  - 集合$\to$群 引入封闭的二元运算与逆元，增加了可加性，可逆性，代数对称性
  - 群$\to$ 向量空间 引入了标量数乘，增加了线形组合关系，生成，依赖，维数，线形映射
  - 向量空间$\to$内积空间 引入内积，增加了 长度，角度，正交，投影
  - 拓扑空间 为空间引入邻近关系，增加了连续性，极限，收敛，开集

- 现代数学研究的不是单一系统，而是研究“一整类在结构上等价的系统”
  - 等构(isomorphism)是指在不关心元素具体是什么的前提下，两个对象拥有一样的结构关系
  - 存在 可逆，且双向保持结构
  - 相似 是特指表示层矩阵，$A=P^{-1}BP$
  
- 脱离线形算子T的空间分解只是代数构造；与T不变子空间相容的直和分解，才反映了算子的内在结构
  - 算子T引入了“动态行为”
    - 线形算子T：V $ \to $ V 带来的不是一个新的集合，而是一个演化规则， 一个行为约束
    - 关心的问题变成：哪些方向被保留了？(kernal,image) 哪些空间在算子作用下是稳定的(不变子空间)
    - 不变子空间$U,T(U) \in U$,如果$V = U \oplus W$,T在V上的行为完全分解为U和W上的行为，才是真正的结构分解
  - 特征空间空间， 每个特征值对应一个不变子空间
  - 广义特征空间 ?
  - 主分解定理 ?
  - Jordan标准形， 极大化的不变子空间直和 ?

- 线形代数既研究线形算子T的内在结构(不变量、等价类、不变子空间)，也研究如何通过合适的表示与变换，使得T在数值与计算意义下尽可能简单，稳定，可用。
  - 结构线形代数，关心T的本质是什么，哪些性质在任何表示下都不变，T在结构上是什么
    - 核心问题有：
      - 不变子空间
      - 特征值/Jordan结构
      - 代数不变量
      - 同构与等价类
    - 典型工具：
      - Jordan分解
      - 主分解定理
      - 谱理论
  - 数值/表示线形代数，他关心T如何被稳定的表示和计算，在有限的精度下，哪些信息是可靠的，“怎么看，怎么算T，才不会被数值误差毁掉”
    - 核心问题有：
      - 条件数
      - 稳定性
      - 误差传播
      - 最优表示
    - 典型工具：
      - SVD
      - QR分解
      - 正交变换
      - 范数最小化
    - 普通映射，不是用来理解世界的结构，而是连接不同的结构
      - 用于表示与建模
        - 坐标变换
        - 编码/解码
        - 特征提取
        - 投影，嵌入，降维
      - 函数空间 $\to$ 数据空间
        - 积分算子
        - 采样算子
        - 观测算子

## 线形映射

- 线形映射T在一组基上的作用，完全确定了T，寻找与T结构相匹配的基，**使其行为显式化**，不同目标对应不同的”最优基“
  - 结构分析目标(结构现代)， 寻找不变子空间的基，广义特征向量基，结果是
    - 对角形/Jordan形
    - 直接反映结构不变量
  - 数值与几何目标(数值现代)， 寻找正交基，奇异向量基，结果是
    - SVD
    - 稳定，可计算
  - 建模/表示目标(普通线形映射)，寻找 稀疏化的基， 低秩结构显式化的基，结果是
    - 压缩
    - 降维
    - 特征提取
- kernal/image
  - 普通线形映射V $\to$ W
    - kernal 表示信息丢失
    - range 表示可达输出
    - rank-nullity 信息守恒
  - 算子，kernal/image是所有高级结构的地基，不变子空间
    - 特征理论从kernal开始，$ker(T-\lambda I) = E(\lambda,T)$,广义特征空间也是kernal的迭代版本
    - Jordan 分解从kernal/range 链条开始 $kerT \subseteq kerT^2 \subseteq \ldots $;$ImT \supseteq ImT^2 \supseteq \ldots $
  - 数值代数
    - 奇异值为0 $\iff$ kernal 非平凡
    - 左奇异空间 $\iff$ range 的正交表示($U\sum V^T,U左奇异向量：输入里哪些方向是重要的，V右奇异向量：这些重要输入方向，在输出空间变成了哪些方向)

- 商空间 V/U 中，元素不再是原来的单个向量，而是向量的等价类；
若 $v-w\in U$，则 v 与 w 代表同一个等价类，
因而在商空间中对应同一个向量。

- 同一矩阵A，既可以看作线形映射T：V$\to$W,也可看作是对偶映射$T^,:W^,\to V^,但他们作用在不同的对象上，语义不同
  - 列视角，CR分解中的C
  - 行视角，

- 线形映射T通过选定一组基，和矩阵同构，该同构保持的是 T 的线性作用语义在坐标层面的表达（保加法，数乘，复合（ST））；线性映射 T 可以
  - 忽略某些方向（核）
  - 合并某些方向（秩下降）
  - 拉伸或压缩方向（特征值大小变化）
  - 在保持自由度的情况下重组方向（旋转 / 等距变换


## 多项式

- 线形代数的结构问题，本质是“在哪个域上做因式分解”；线形算子T的结构分析以零空间(kernal)为基础， 这与多项式通过根来分析结构是类比的
  - 在复数域上，特征多项式完全分解，因子算子可以完全分解为由特征值及其广义零空间构成的Jordon结构
  - 在实数域， 某些特征值不可见，只能以对应的二次不可约块出现，正如实系数多项式只能分解为一次与二次因子

- $r(t) = t^2+bt+c(b^2<4c)$在$\mathbb{R}$没有实数根，对应一对共轭复根($\lambda,\bar{\lambda}$)
  - r(T)的零空间，即$r(T) = T^2+bT+c(b^2<4c) = 0$,T在ker(r(T))里的行为像“复数乘法/旋转缩放”，而不像特征向量那样的一维伸缩
  - ker(r(T))是实空间的维度是2k，在“Jordan/广义结构”上；最小多项式中出现这一类因子会产生2x2的基本块，如果是$r(t)^k,则会对应一个2k维的实数广义块。

## 特征值和特征多项式

- 最小多项式的结构，决定了能不能选对角基/上三角基， 它决定了算子内部的**”零空间链“**，只能有一次因子
  - $m_T(t) = \prod_{i}({t-\lambda_i})$,因子没有重复，表明($T-\lambda_i)一次就能把对应不变子空间“杀干净”
    - 构造对角矩阵，只需要使用特征向量
- $m_T(t) = \prod_{i}({t-\lambda_i})^{k_i} \quad  \exists k_i \geq 1$, 表明($T-\lambda_i)一次不够，必须用高次零空间，需要广义特征向量，此时一定能找到一条jordan链
$ v_k,v_{k-1},\ldots,v_1,满足 \\$

$$
\begin{aligned}
  (T-\lambda I)v_1 &= 0 \\
  (T-\lambda I)v_2 &= v_1 \\
    &\vdots \\
    (T-\lambda I)v_{k} &= v_{k-1} \\
\end{aligned}
$$

- 在对应特征值$\lambda$ 的广义特征空间上，算子 T 的行为 = $\lambda I$ 的伸缩 + 一个幂零算子(沿链向下流动)”。
- 构造上三角矩阵的基向量都是属于$ker(T-\lambda I)^k$的广义特征向量，按jordan 链结构组成

- ST = TS => $(T-\lambda I)S = S(T-\lambda I) =>(T-\lambda I)^kS = S(T-\lambda I)^k$, 即S不改变T的零结构，广义特征空间。
  - S，T共享不变旗，则可同时上三角化
  - S，T可对角化，共享特征空间=广义空间，可同时对角化

## 复空间算子

- 之所以关注标量域，是因为线形算子的结构分析最终依赖“**在该域中是否存在足够的特征值**”，即最小多项式的一次因子，来作为分解整个空间的结构锚点。
  - 在$\mathbb R$上，$t^2+1$是原子的，看不见内部结构
  - 在$\mathbb C$上，$t^2+1 =(t - i)(t + i)$,结构被“解锁”

- Jordan理论的前提，T有泛特征向量基$\iff m_T(t) = \prod_{i}({t-\lambda_i})^{k_i}$最小多项式分解为一次因子 $\iff V = \bigoplus_{\lambda} G_\lambda(T)$

- 幂零算子 $T^m =0,m \leq dim(V)$ =>$T^{dim(V)} = 0$ => ***0*** 是唯一特征值 $\iff$
  - $m_T(t) = z^m$
  - 有泛特征向量基，使得

$$
\begin{pmatrix}
    0\quad \phantom{*}\quad *\\
    \phantom{0}\quad \ddots\quad \phantom{*}\\
    0\quad \phantom{0}\quad 0\\
\end{pmatrix}
$$

- 代数重数$m_{a\lambda} = dim(ker(T-\lambda_i)^{dim(V)})$, 几何重数$m_{g\lambda} = dim(ker(T-\lambda_i))$, 即$dim(G(T,\lambda)),dim(E(T,\lambda))$
  - 代数重数 也等于特征多项式$det(\lambda I -A) =(z - \lambda_1)^d_1 \ldots(z - \lambda_m)^d_m$代数根数
  - 无论 Jordan 块有多大，它只产生 1 个特征向量
  - Jordan 块，特征值0，代数重数3，几何重数2，

$$
\begin{pmatrix}
  0\quad 1\quad 0 \\
  0\quad 0\quad 0 \\
  0\quad 0\quad 0
  \end{pmatrix}

$$

- 设特征值$\lambda$,他的Jordan块大小为$s_1 \geq s_2 \geq \ldots \geq s_k$(k个块)
  - 最大块的大小$s_1 =$最小多项式中$(x-\lambda)的指数
  - $s_2,s_3,\ldots,s_k$是其他块的大小由$dim(ker(A - \lambda I)^j)$的增长决定

$$
  n_j := dim(ker(A-\lambda I)^j) \\
  s_j := n_j -n_{j-1}
$$

- Trace 迹
  - tr(AB) = tr(BA) or tr(ABC) = tr(CAB) = tr(CAB)( 按顺序循环)
  - $tr(P^{-1}AP) = tr(A)$ 换基不改变
  - $tr(A) = \sum_{i=1}^n \lambda_i$

## 内积空间及内积算子

- 内积空间是“把线形代数语义话、几何化”的最小结构
  - 向量 由抽象元素 变成 有方向和大小的元素
  - 正交 => 线形无关 (反之不成立)
  - 子空间 由集合变成 几何平面
  - 投影 变成最小误差近似
  - 分解 变成最优分解

- 内积空间，如果一个T可以上三角化，一定存在正交基使其矩阵上三角化， 过程为Schur 分解(gram-schimid过程中需要保证不变子空间链)。

- 正交投影是唯一的，因为$V= W \oplus W^\perp$
  - 如果$e_1,e_2, \ldots, e_m$是U的正交基，则$P_Uv = \langle v,e_1\rangle e_1 +\langle v,e_2\rangle e_2+\ldots+\langle v,e_m\rangle e_m$
  - 到子空间的最小距离  $||v - u || \geq ||v -P_U(v)||$ 

- Riesz 表示定理 

$$
    \text{for each} v \in V,define \;\varphi_v \in V^{'} by \\
    \varphi_v(u) =\langle u,v\rangle \\
     \in V,v\to\varphi_v \text{is a one-one function from V to }V^{'}

$$

- 伪逆$T^\dagger w=(T|_{(nullT)^\perp})^{-1}P_{rangeT}w$

- 伴随算子$T^*$, $\langle Tv,w\rangle _W = \langle v,T^*w\rangle _V$
  - 由Rissez定理，v \to \langleTv,w\rangle 是一个线形泛函，一一对映 $\langle v,v^{'}(w)\rangle$,即$T^*w$
  - \langle Tv,w\rangle,是在输出空间W中，对输出Tv在w方向上的度量；若要把这一度量解释为输入向量v的性质，就必须将度量通过伴随算子换回输入空间V，即$\langle v,T^*w\rangle$
  - $null(T^*) =(rangeT)^\perp$ ,$null(T^*)$将w映射为0，意味着\langle Tv,w\rangle = 0 对任意v 

- 自伴随算子 $T = T^*, \langle Tv,w\rangle = \langle v,Tw\rangle$
  - 这个算子对任何方向的作用，都可以完全由一个“内部能量/二次度量”来解释，换言之，它不区分输入和输出的测量位置，T本身就是度量结构，因为可以自然的定义$Q(v) = \langle v,Tv\rangle$
  - 自伴随算子的特征值都是实数
  - $\langle Tv,v\rangle$是实数，对所有v,T是v的几何本体属性
  - $T^2 +bT +cI(b^2<4c) 是可逆算子， 最小多项式没有二次项因子

- normal 算子T，$TT^* = T^*T$, 先变换后拉回度量 = 先拉回度量再作用，意味着T不改变内积几何的正交可分解结构，几何可以被选择成一组正交主方向，使得变换在这些方向上彼此独立。
  - 算子作用后，不保角，不保长，但保证存在一组正交方向(特征方向)上 a.使得变换后仍然正交；b.同一特征值模对应方向上，原来相等的，作用后仍然相等；c .在这一组正交方向张成的分解下上，长度，角度，正交，投影/分解关系保持不变，但其他方向不保证)
  - ||Tv|| = ||T^*v||
  - normal 算子在特定正交方向(特征方向)独立演化，只允许拉伸/压缩 (旋转(复空间))
  - 如果T为normal， $V = null T \oplus rangeT$
  - 如果T为normal，$T-\lambda I$ 也会normal
  - $Tv = \lambda v \iff T^*v = \bar{\lambda}v$,特征方向同时是作用方向和度量方向；在这些方向上只相差复共轭。
  - 如果T为normal，$T = A+iB  A = \frac{T+T^*}{2},B =\frac{T-T^*}{2i} A=A^*, B=B^*$ 
    - AB =BA ,A：实几何，拉伸/压缩，能量/方差/曲率等；B：虚几何：相位变化/旋转生成元(复意义)；先看强弱，再看旋转 和 先看旋转在看强弱，得到的是一套主方向。(**相位不是几何旋转，而是复标量的角度，不影响向量方向**)

- 实谱理论 F=R
  - 对于自伴随算子T， $T = T^*, \langle(T- \lambda I)^2v,v\rangle = ||(T-\lambda I)v||^2 => ker(T-\lambda I) = ker(T-\lambda I)^2 $, 没有高幂次0空间
  - 最小多项式只包含唯一一次因子，$m_t(z)=(z - \lambda_1) \ldots(z -\lambda_m) , \lambda_m \in \mathbb{R}$为特征值
  - T 有足够的特征向量，构成正交基；且T可以有对角矩阵

- 复谱理论 F=C
  - T is normal

- positive 算子， 定义了一种“处处非负”的二次几何结构。
  - $\iff$ 所有特征值为非负
  - 有唯一正平方根
  - T 有一个正平方根 $\iff$ T 有一个自伴随平方根 $\iff T= R^*R \iff$T 为正算子

- 等距映射， 保长度 ||Su|| =||u||，保角度\langleSu,Sv\rangle = \langleu,v\rangle,保正交
  - $M(S,(e_1,e_2,\ldots,e_n),(f_1,f_2,\ldots,f_m))$列形成$F^m$正交列表

- 酉算子unitary
  - $S^*S = SS^*$
  - $S^{-1} = S^*$
  - $M(S,(e_1,e_2,\ldots,e_n))$行标准正交基$F^n$
  - $|\lambda| =1$

- T = QR factorization；$T：V\to W = QR,(Q:U\to W $等距映射；$R：V\to U$ T的代数结构 ,通常V和U等维
  - 语义上指：现在空间U中完成T代数结构的变换R(线形依赖，长度 顺序依赖等)，然后在等距映射到新的空间
  - R 必定有特征值；并且在“QR 构造所选的那组正交基”下，R 被表示为上三角矩阵；但这并不意味着 R 在某个正交基下具有算子意义上的不变子空间链。(R的上三角是写出来的，不是他本来就有的)
  - 有算子不变子空间链 ⇒ 可以上三角化；即使没有算子不变子空间链，也可以通过顺序构造(如 QR)
得到表示层面的上三角矩阵；

- Cholesky factorization：$B=R^*R$(B正定positive definitive 矩阵，R对角为正数的上三角)
  - $B=A^*A =(QR)^*(QR) = R^*Q^*QR = R^*R$

- $T^*T$可用于评估T在不同方向上，对向量“长度(能量)”的作用强度 $\langle T^*Tx,x\rangle = \langle Tx,Tx\rangle =||Tx||^2$，$T^*T$不关心Tx指向哪里，只关心它有多大

- SVD decomposition: T：V\to W, $ T = U \sum V^*$ ;方向V，强度$\sum$,输出语义(U)
  - $Tv = s_1\langle v,e_1\rangle f_1 + \ldots+s_m\langle v,e_m\rangle f_m(e_m in V,f_m in W$(标准正交列) 
  - $T^*v = s_1\langle w,f_1\rangle e_1 + \ldots+s_m\langle vw,f_m\rangle e_m(e_m in V,f_m in W$(标准正交列) 
  - $T^\dagger v = \langle w,f_1\rangle e_1/s_1 + \ldots+ \langle vw,f_m\rangle e_m/s_m$
  - $e_m 为T^*T$正交标准特征向量，即 $T^*Te_k = s_k^2e_k$
  - $f_m = Te_k/s_k，$,因为$\langle f_j,f_k\langle =0 if j \neq k; =1 if j =k$
  - 任意线形算子T，分解为： 先选方向(方向结构) \to 纯拉伸(强度结构) \to 再换方向(坐标无关表示)， 三件互不干扰。
  - 矩阵形式 $A = BDC^* \quad A(F^{p*n},rankA = m \geq 1)$; 存在 $B(F^{p*m})$标准正交列($f_1,\ldots,f_m$；mxm 正数对角矩阵D($s_1,\ldots,s_m$)， nxm C，正交标准列($e_1,\ldots,e_m$)

- polar decomposition: $T = S \sqrt{T^*T}$ $T \in \mathbb L(V)$, $S \in \mathbb L(V)$ unitary operator.

## 双线形

- $M(\beta)_{j,k} = \beta(e_j,e_k)$, $M(\beta(u,v)) = M(u^T)M(\beta)M(v)$
  - $\alpha(u,v) = \beta(u,Tv)$ and $\rho(u,v) = \beta(Tu,v)$ ,

$$
    M(\alpha) = M(\beta)M(T) \\
    M(\rho) = M(T)^tM(\beta)
$$
  - 换基

$$
    A = M(\beta,(e_1,\dots,e_n)), B= M(\beta,(f_1,\dots,f_n))\\
    C= M(I,(e_1,\dots,e_n),(f_1,\dots,f_n)) \\
    A = C^tBC
$$

- 对称双线形(symmetric)
  - 交替二次项(alternating)：$\alpha(v,v) = 0,\alpha(u,v) = - \alpha(v,u)  $
  - $V^{(2)}= V_{sym}^{2} \oplus V_{alt}^{(2)}$

- v⟼β(⋅,v), 此时$\beta$ 内积空间 riesz表示， 或通过$\beta$指标下降， v通过$\beta$映射成线形泛函
对每个固定的u,$v \to\rho(u,v) $右边是一个线形泛函; $V \cong V^{'}$同构,存在唯一向量Tu使得
$\rho(u,v) = \beta(Tu,v) \forall v$

- 二次型 quadratic forms ：$q:V\to F$  线形泛函，
  - 存在唯一对称双线形$\rho$ on V，$2 \rho(u,v) = q(u+v) - q(u)-q(v)$
  - 存在基$e_1,\dots,e_n$ of V$ 使得$q(x_1e_1+\dots+x_ne_n) = \lambda_1x_1+\dots+\lambda_nx_n$, F=R 且为内积空间，可选一组正交基。
