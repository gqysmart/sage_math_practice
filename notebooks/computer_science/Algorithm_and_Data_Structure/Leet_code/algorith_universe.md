# Algorithm Universe v1.0
Author: Qiyun Ge  
Goal: Build a unified mental model of the algorithm world  
Core idea: Problem → State → Transition → Structure → Algorithm

---

# 0. 核心世界观

所有算法问题，本质只有两件事：

1. 如何表示世界（State Representation）
2. 如何在世界中移动（State Transition）

算法 = 在状态空间中的搜索 / 推理 / 优化过程

---

# 1. 算法世界的 6 大类问题（工程抽象）

## 1️⃣ Search / Traversal（搜索 / 遍历）

本质：
在状态空间中找到目标状态

状态：
图节点 / 树节点 / 网格位置 / 组合状态

迁移：
邻接移动

典型算法：
- DFS
- BFS
- Backtracking

典型问题：
- Number of Islands
- Word Search
- Path existence
- Graph connectivity

---

## 2️⃣ Ordering / Selection（排序 / 选择）

本质：
建立元素间的顺序关系

状态：
元素集合

迁移：
比较、交换、筛选

典型算法：
- Sort
- Quickselect
- Heap
- Top-K

典型问题：
- 排序
- 第 K 大
- Median stream

---

## 3️⃣ Dynamic Programming（动态规划）

本质：
在时间维度上的状态图搜索

状态：
子问题解

迁移：
dp[i] = f(dp[i-1], dp[j], ...)

特征：
- 最优子结构
- 重叠子问题
- 状态压缩

典型问题：
- LIS
- Knapsack
- Word Break
- Edit Distance

---

## 4️⃣ Greedy（贪心）

本质：
每一步局部最优 → 全局最优

状态：
当前决策位置

迁移：
不可回退选择

典型问题：
- Interval scheduling
- Huffman coding
- Minimum spanning tree

---

## 5️⃣ Math / Structural（数学 / 结构计算）

本质：
问题本身是代数结构

状态：
矩阵 / 概率模型 / 数论对象

迁移：
公式推导 / 运算

典型问题：
- PCA
- Fast power
- GCD
- Probability
- Bit manipulation

---

## 6️⃣ Data-Structure Driven（数据结构驱动）

本质：
通过结构压缩状态空间

状态：
被结构化的集合

迁移：
结构操作

典型结构：
- Trie
- Segment Tree
- Union-Find
- LRU cache
- Heap

---

# 2. 更高层抽象（3 类）

## A. Search problems
- DFS / BFS
- Backtracking
- DP
- Graph

本质：
在状态空间中找路径

---

## B. Optimization problems
- DP
- Greedy
- Linear programming

本质：
在目标函数中找最优值

---

## C. Structural problems
- Math
- Data structures
- Algebra

本质：
利用结构直接推导解

---

# 3. 理论计算机科学抽象（2 类）

## 1. Decision problems
输出：
Yes / No

例：
- 是否存在路径
- 是否可分割
- 是否满足条件

---

## 2. Optimization problems
输出：
Max / Min

例：
- 最短路径
- 最大利润
- 最小编辑距离

---

# 4. 统一模型（最核心）

所有算法可以统一为：

Algorithm =
    State Representation
    + Transition Function
    + Search Strategy
    + Pruning / Optimization

---

# 5. 状态空间模型

## State
问题在某一时刻的描述

例：
- grid position
- dp index
- tree node
- subset mask

---

## Transition
状态如何变化

例：
- graph edges
- dp recurrence
- swap / merge
- math transform

---

## Search strategy
如何探索状态空间

- DFS
- BFS
- DP
- Greedy

---

## Pruning
如何减少状态空间

- memoization
- heuristic
- bounding
- monotonic structure

---

# 6. 算法本质公式

Algorithm solving process:

Problem
→ Model the state
→ Define transitions
→ Explore the state space
→ Prune
→ Reach solution

---

# 7. 一切题目的统一视角

任何题目，都可以问 5 个问题：

1. 状态是什么？
2. 状态空间大小？
3. 状态如何转移？
4. 有没有重复状态？
5. 能不能剪枝 / 压缩？

---

# 8. 心智模型（最重要）

算法不是代码技巧

算法是：

- 状态建模能力
- 状态空间控制能力
- 转移设计能力
- 抽象能力

---

# 9. 最终结论

所有算法，本质只有一个：

在“状态图”上的移动

不同算法只是：

- 移动方式不同
- 状态表示不同
- 剪枝方式不同
- 是否有数学结构

---

# 10. 下一步升级方向

Algorithm Universe v2 目标：

- 状态压缩理论
- 图模型统一
- DP = DAG traversal
- Greedy = single path traversal
- Math = closed-form traversal
- Data structure = compressed state traversal

最终统一为：

Everything is state-space navigation.
