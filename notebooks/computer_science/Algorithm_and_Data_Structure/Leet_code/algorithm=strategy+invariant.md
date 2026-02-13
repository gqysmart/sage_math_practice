# Algorithm = Strategy + Invariant
Unified Algorithm Note v1.0  
Author: Qiyun Ge

---

# 0. 核心命题

所有算法都可以统一为：

Algorithm =
    Strategy
    +
    Invariant

---

# 1. Strategy（策略）

作用：
决定算法“如何移动”。

本质：
- 搜索顺序
- 决策规则
- 状态转移方式

控制：
算法的动态行为。

典型形式：

- DFS：深度优先策略
- BFS：层序策略
- Greedy：局部最优策略
- DP：拓扑更新策略
- Dijkstra：最小代价优先策略
- A*：启发式策略

---

# 2. Invariant（不变量）

作用：
保证算法“不会偏离正确性”。

本质：
在执行过程中始终保持成立的性质。

控制：
算法的稳定性与正确性。

注意：

不是所有算法都显式写出 invariant  
但所有正确算法都隐含 invariant

---

# 3. invariant 的三种来源

## 3.1 结构不变量（Data Structure Invariant）

来源：
数据结构的组织方式

例：

### Heap
不变量：
parent ≤ children

### Monotonic Stack
不变量：
单调递增 / 单调递减

### Union-Find
不变量：
树形连通结构

### Trie
不变量：
前缀路径一致

作用：
结构维护 → solution 自然浮现

---

## 3.2 数学不变量（Mathematical Invariant）

来源：
数学定理 / 代数结构

例：

### Euclid
gcd(a, b) = gcd(b, a mod b)

### Fast Power
result × base^k = 原始值

### PCA
协方差矩阵对称性 + 特征结构

作用：
推导过程保持等式成立

solution 被“推导”出来

---

## 3.3 状态不变量（State Invariant）

来源：
状态建模 / DP / 图遍历

例：

### DP
dp[i] 表示前 i 个的最优解

不变量：
dp[0…i-1] 已正确

### BFS
队列中始终保持“同层结构”

### Dijkstra
出堆节点距离已确定为最短

作用：
搜索过程不会回退或失效

---

# 4. 统一视角

Algorithm 本质：

Controlled State Evolution

即：

在状态空间中  
通过策略驱动  
在不变量约束下  
逐步逼近 solution

---

# 5. solution 如何产生

| 类型 | solution 产生方式 |
|---|---|
| Search-driven | 被搜索到 |
| Math-driven | 被推导出 |
| Structure-driven | 被维护出来 |
| Simulation-driven | 被逼近 |

但底层统一为：

Strategy + Invariant

---

# 6. Strategy vs Invariant 的关系

Strategy：
让算法“动”

Invariant：
让算法“不乱”

二者关系：

Strategy 决定路径  
Invariant 限制路径

---

# 7. 状态空间视角

state space traversal =
    strategy-driven
    +
    invariant-constrained

即：

遍历方向来自策略  
遍历边界来自不变量

---

# 8. 更高层抽象

Computation =
    Evolution under constraints

其中：

- Evolution → Strategy
- Constraints → Invariant

---

# 9. 数据结构、算法、数学的统一

| 层级 | 本质 |
|---|---|
| 算法 | strategy 主导 |
| 数据结构 | invariant 主导 |
| 数学 | invariant = 定理 |
| DP | state invariant |
| graph | reachable invariant |

---

# 10. 复杂度来源（重要）

复杂度 ≈

state space size
×
strategy efficiency
×
invariant strength

剪枝 / DP / 结构优化  
本质：

加强 invariant  
减少可达状态

---

# 11. 最终统一模型

Algorithm =
    Strategy (state transition rule)
    +
    Invariant (constraint that must hold)

执行过程：

state₀
→ transition
→ state₁
→ transition
→ state₂
...
在 invariant 约束下收敛到 solution

---

# 12. 终极结论

所有算法本质是：

在约束下的状态演化。

Strategy 控制“如何走”  
Invariant 保证“不会错”

solution 是：

演化过程的稳定结果。
