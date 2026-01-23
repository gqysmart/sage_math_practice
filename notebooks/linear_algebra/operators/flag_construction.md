# Flag construction

## 找到一个特征向量

取特征对：
$$
Tv_1 = \lambda_1 v_1
$$
定义：
$$
V_1 = span {v_1}
$$
结论：
$$
T(V_1) \subseteq V_1
$$

## 2. 第二步：进入商空间（剥离已处理层）

构建商空间：
$$
V/V_1
$$
定义诱导算子：

$$
\bar T([x]) = [T(x)] \\
[x] = x+W = \{x+w|w \in W\}
$$
对等价类[x],先选一个代表元，作用T，再取结果的等价类。

良定义性理由：(同一个等价类选用不同代表得到的[T(x)]不一样，$ \bar T$就不是良定义)
$$
if \quad (x-y) \in V_1,\\
T(x-y) \in V_1
$$

## 3. 第三步：在商空间中在找“特征方向”

由于$V/V_1$仍是复数向量空间，存在：
$$
\bar T[v_2] = \lambda_2[v_2]
$$
按商空间等号的定义，这等价于：
$$
Tv_2 -\lambda_2 v_2 \in V_1, \\
Tv_2 = \lambda_2 v_2 + w_1, w_1 \in V_1
$$
定义
$$
V_2 = span\{V_1,V_2\}
$$
则
$$
T(V_2) \subseteq V_2
$$
最终得到完整的flag：
$$
0 \subset V_1 \subset V_2 \subset \dots \subset V_n = V
$$

## 与上三角矩阵的等价关系

选基$(v_1, v_2,\dots,v_n)$ 由于
$$
Tv_k \in span\{v_1,dots,v_k\}
$$