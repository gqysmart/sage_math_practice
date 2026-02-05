# Structure-First Problem Solving  
## 数据结构抽象决定问题的可解性与算法形态

> 核心结论：  
> **问题解决的决定性因素，不是算法技巧，而是你用什么数据结构抽象来描述问题。**

---

## 1. 根本判断

### 1.1 核心命题

> **Algorithm works *because* the data structure makes it possible.**

换句话说：

> **算法只是结构上的运动规则，  
> 结构决定了问题的可见性、可达性与复杂度下界。**

---

### 1.2 一个等式（方法论级）

Program
= Algorithm ∘ Structural Abstraction ∘ Execution Model

其中：

- **Structural Abstraction** 是决定性因素
- Algorithm 是次级的（在结构空间内选择路径）
- Execution Model 决定常数与工程表现

---

## 2. 问题 = 结构表达

### 2.1 问题的真实形态

任何计算问题，都可以还原为：

Problem = (Objects, Relations, Constraints)

而 **数据结构抽象** 的本质是：

> **用有限的计算原语，忠实表达 Objects + Relations**

---

### 2.2 同一问题，不同结构 = 不同问题

| 问题 | 结构选择 | 结果 |
|----|----|----|
| Duplicate Detection | Sequence | O(n²) |
| Duplicate Detection | Set | O(n) |
| Range Sum | Raw Sequence | O(n) per query |
| Range Sum | Prefix Sum | O(1) per query |
| Top-K | Sorting | O(n log n) |
| Top-K | Heap | O(n log k) |

> **复杂度的跃迁来自结构升级，而非算法技巧。**

---

## 3. 常用结构抽象（Problem Modeling Primitives）

### 3.1 Sequence（顺序）

**语义**
- 有序
- 位置有意义

**信号**
- index / time / window
- prefix / suffix

**算法范式**
- scan
- two pointers
- sliding window
- DP

---

### 3.2 Set / Map（成员 / 映射）

**语义**
- 存在性
- 频次
- key → value

**信号**
- seen?
- count
- lookup

**实现**
- hash table
- balanced BST
- array index

---

### 3.3 Graph（关系 / 状态空间）

**语义**
- 状态 + 转移
- 可达性

**信号**
- path
- dependency
- reachability

**算法范式**
- DFS / BFS
- shortest path
- flow / cut

---

### 3.4 Tree（层级结构）

> Tree ⊂ Graph

**语义**
- 层级
- 单父
- 递归

**信号**
- ancestor
- subtree
- divide

---

### 3.5 Stream（在线 / 访问受限）

**语义**
- 单向
- 不可回溯
- 内存受限

**信号**
- one-pass
- online
- approximate

**算法**
- sketch
- bloom filter
- reservoir sampling

---

### 3.6 Heap / Priority（最值）

**语义**
- extremum
- priority

**信号**
- top-k
- min / max

---

## 4. 算法的真实角色

### 4.1 算法不是“解决问题”

> **算法是在既定结构中执行状态转移的规则。**

算法回答的只是：

- 如何遍历？
- 如何更新？
- 如何选择？

---

### 4.2 算法选择是“局部自由度”

一旦结构选定：

- 可用算法范式通常 < 3
- 很多算法“自然浮现”

---

## 5. 下界来自结构，而非算法

### 5.1 信息论下界

- 是否存在重复 → Ω(n)
- 是否排序 → Ω(n log n)

这些下界源自：

> **结构所允许的信息暴露速度**

---

## 6. 结构优先的解题流程（Checklist）

1. 问题真正关心的是什么？
   - 顺序？
   - 存在？
   - 关系？
   - 层级？
   - 时间？
   - 最值？

2. 是否可以丢弃原始输入结构？

3. 是否存在结构变换？
   - sequence → set
   - graph → tree
   - raw data → prefix / index

4. 在该结构下，算法是否“自然成立”？

---

## 7. 重要纠偏

### 7.1 不是“用最强结构”

- 结构必须 **最小充分**
- 过强结构会：
  - 增加复杂度
  - 模糊问题语义
  - 降低可维护性

---

### 7.2 Hash Table 不是问题结构

- Hash table 是 **Set / Map 的实现**
- 问题建模应停留在抽象层

---

## 8. 终极原则（宣言级）

> **问题一旦被正确结构化，  
> 算法只是必然的后果。**

或更激进地说：

> **结构决定可能性空间，  
> 算法只是其中的一条轨迹。**

---

## 9. 个人注记（可持续扩展）

- [ ] 为每一道题写一句「结构判断」
- [ ] 标注是否存在结构变换
- [ ] 记录“结构选错”的失败案例
- [ ] 维护一个「结构 → 典型题型」映射表

