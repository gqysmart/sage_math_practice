# Algorithm Modeling Notes  
## From Problem → Structure Abstraction → Algorithm Paradigm

> 核心原则：  
> **算法不是从“数据结构”开始，而是从“问题的结构语义”开始。**

---

## 0. 总览：常用问题建模原语（Core Structural Abstractions）

| 抽象结构 | 核心语义 | 典型关键词 |
|---------|----------|------------|
| Sequence | 顺序 / 时间 / 位置 | index, prefix, window |
| Set / Map | 存在 / 频次 / 映射 | seen?, count, lookup |
| Graph | 状态 / 转移 / 关系 | reachability, path |
| Tree | 层级 / 递归 | parent, subtree |
| Stream | 在线 / 不完全信息 | one-pass, memory limit |
| Heap / Priority | 最值 / 调度 | min/max, top-k |

---

## 1. Sequence（序列）

### 1.1 抽象定义
- 有序
- 可重复
- 位置有意义（index-based）

### 1.2 建模信号
- “第 i 个元素”
- “连续子数组”
- “前缀 / 后缀”
- “随时间变化”

### 1.3 常见算法范式
- Linear scan
- Two pointers
- Sliding window
- Dynamic Programming（DP）
- Prefix sum

### 1.4 典型问题
- Maximum subarray
- Longest substring
- Range sum
- LIS / LCS

---

## 2. Set / Map（成员与映射）

> 抽象层：Set / Map  
> 实现层：Hash table, BST, Array index

### 2.1 抽象定义
- Set：是否存在
- Map：key → value

### 2.2 建模信号
- “是否出现过？”
- “频率 / 次数”
- “一一映射关系”

### 2.3 常见算法范式
- Hash-based lookup
- Frequency counting
- Deduplication
- Invariant maintenance

### 2.4 典型问题
- Contains duplicate
- Two Sum
- Anagram
- Majority element

---

## 3. Graph（关系 / 状态空间）

### 3.1 抽象定义
- 节点 = 状态
- 边 = 转移 / 关系

> Graph = 状态空间 + 可达性

### 3.2 建模信号
- “能不能到达？”
- “依赖顺序”
- “转换规则”
- “路径 / 最短 / 最优”

### 3.3 常见算法范式
- DFS / BFS
- Shortest path (Dijkstra, Bellman-Ford)
- Topological sort
- Union-Find
- Flow / Cut

### 3.4 典型问题
- Course schedule
- Network flow
- Word ladder
- Grid traversal

---

## 4. Tree（层级结构，Graph 的特例）

### 4.1 抽象定义
- Graph
- 无环
- 单父节点（rooted tree）

### 4.2 建模信号
- “父 / 子 / 祖先”
- “子问题结构相同”
- “天然递归”

### 4.3 常见算法范式
- DFS recursion
- Divide & Conquer
- Tree DP
- Post-order / Pre-order

### 4.4 典型问题
- Binary tree traversal
- Lowest common ancestor
- Expression tree
- Segment tree

---

## 5. Stream（流模型）

> Stream 不是数据结构，而是**计算模型约束**

### 5.1 抽象定义
- 只能顺序读取
- 不能回溯
- 数据可能无限
- 内存受限

### 5.2 建模信号
- “只能看一遍”
- “实时输入”
- “在线决策”

### 5.3 常见算法范式
- One-pass algorithms
- Sketch / Bloom Filter
- Reservoir sampling
- Online greedy

### 5.4 典型问题
- Duplicate detection (approx)
- Frequency estimation
- Sliding window stream
- Online statistics

---

## 6. Heap / Priority（最值与调度）

### 6.1 抽象定义
- 动态维护最小 / 最大元素
- 不关心全序，只关心 extremum

### 6.2 建模信号
- “当前最小 / 最大”
- “Top-K”
- “调度 / 优先级”

### 6.3 常见算法范式
- Priority queue
- Greedy + heap
- Incremental optimization

### 6.4 典型问题
- Kth largest element
- Merge K sorted lists
- Task scheduling
- Dijkstra（实现层）

---

## 7. 重要纠偏（非常关键）

### 7.1 Tree ⊂ Graph
- Tree 是 graph 的受限特例
- 不要并列理解

### 7.2 Hash table ≠ 问题模型
- Hash table 是 **Set / Map 的实现**
- 问题建模应停留在抽象层

### 7.3 顺序扫描 ≠ 算法选择
- 很多问题的 Ω(n) 下界来自信息论
- 顺序扫描是“不可避免”，不是“偷懒”

---

## 8. 通用建模流程（你以后所有题都能用）

1. 输入数据的**原始形态**是什么？
2. 问题真正关心的是：
   - 顺序？
   - 存在？
   - 关系？
   - 层级？
   - 时间？
3. 能否丢弃原始结构，转化为更合适的抽象？
4. 再选择具体数据结构与算法实现

---

## 9. 一句话原则（核心）

> **算法不是“选数据结构”，  
> 而是先识别问题的“结构抽象”，  
> 再选择合适的数据结构作为实现。**

