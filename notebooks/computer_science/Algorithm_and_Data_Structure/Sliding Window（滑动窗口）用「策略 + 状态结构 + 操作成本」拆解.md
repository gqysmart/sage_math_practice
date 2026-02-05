# Sliding Window（滑动窗口）用「策略 + 状态结构 + 操作成本」拆解

> 目标：用同一套骨架理解滑动窗口为什么快、什么时候用 deque / hash / heap / tree。

---

## 0. 什么是 Sliding Window？

在序列（数组/字符串）上维护一个**连续区间 [L, R]**，随着 R 右移（扩张）和 L 右移（收缩），
**在移动中实时维护窗口内的某种性质**（和/最大值/计数/合法性…）。

典型问题：
- 固定长度窗口最大值
- 最长无重复子串
- 满足某约束（和 ≤ K / 至多 K 种字符）的最长子数组

---

## 1. 三要素拆解

### 1.1 策略（Strategy）
- R 逐步右移：**扩张窗口**
- 若违反约束：移动 L：**收缩窗口**
- 在每个时刻用当前窗口更新答案

> 本质：**局部维护 + 在线更新**（不用回退，不用全局重算）

---

### 1.2 状态结构（State Structure）
根据“窗口里要维护什么”选择：

| 要维护的性质 | 状态结构 |
|---|---|
| 元素频次/是否重复 | hash map / array 计数 |
| 窗口最大/最小 | **monotonic deque** |
| top-K / 动态最值 + 删除 | heap（常配 lazy deletion） |
| 有序关系/前驱后继 | balanced tree / skiplist |

---

### 1.3 操作成本（Operation Cost）
滑窗的高效来自两个不变量：

1) **每个元素最多进窗口一次、出窗口一次**  
2) 每次更新只做**局部 O(1) 或 O(log n)** 操作

因此总复杂度通常是：
- O(n)（deque/hash）
- 或 O(n log n)（heap/tree）

---

## 2. 经典模式一：固定长度窗口最大值（Deque 最强）

**问题**：给定数组 nums，窗口大小 k，输出每个窗口的最大值。

### 策略
- R 右移，元素入窗口
- L 跟随 R 保持窗口长度为 k
- 每一步读出窗口最大值

### 状态结构
- **单调递减 deque（存索引）**
  - 队头：当前窗口最大值索引
  - 入队前：从队尾弹出所有更小元素（它们不可能再成为最大）

### 操作成本
- 每个元素最多：
  - 入 deque 一次
  - 被弹出一次
- 总操作 O(n)

### Python 伪码
```python
from collections import deque

def maxSlidingWindow(nums, k):
    dq = deque()  # 存索引，维护单调递减
    ans = []

    for r, x in enumerate(nums):
        while dq and nums[dq[-1]] <= x:
            dq.pop()
        dq.append(r)

        if dq[0] <= r - k:
            dq.popleft()

        if r >= k - 1:
            ans.append(nums[dq[0]])

    return ans
为什么不用 heap / 红黑树？
因为策略只需要“窗口最大值”，deque 能把操作压到 O(1) 均摊，比 O(log n) 更优。

3. 经典模式二：最长无重复子串（Hash 计数）

问题：最长子串，要求所有字符不重复。

策略

R 扩张

若出现重复字符 c：移动 L，直到窗口内 c 的计数 ≤ 1

状态结构

count[char]（hash 或 128/256 数组）

操作成本

每个字符：

R 进窗口一次

L 移出一次

总体 O(n)

def lengthOfLongestSubstring(s):
    cnt = {}
    l = ans = 0

    for r, ch in enumerate(s):
        cnt[ch] = cnt.get(ch, 0) + 1
        while cnt[ch] > 1:
            cnt[s[l]] -= 1
            l += 1
        ans = max(ans, r - l + 1)

    return ans


关键：策略是“合法性维护”，状态是“频次表”，操作是 O(1)。

4. 什么时候需要 Heap / Tree？

当窗口需要更复杂能力：

需求	推荐结构
动态 top-K	heap
窗口中位数	两个 heap
需要删除任意元素 + 有序	balanced tree / skiplist
复杂区间统计	segment tree
例：滑窗中位数（Two Heaps）

状态：max-heap（左半）+ min-heap（右半）

操作：插入/删除/平衡 → O(log k)

总复杂度：O(n log k)

deque 不行，因为“中位数”不是单调性质。

5. 一眼选结构的判断表
窗口需求	策略核心	状态结构	复杂度
最大/最小	单调维护	deque	O(n)
去重/频次	合法性维护	hash	O(n)
top-K	选择最值	heap	O(n log k)
中位数	平衡两侧	two heaps	O(n log k)
有序关系	前驱/后继	tree/skiplist	O(n log k)
6. 为什么 Sliding Window 通常是 O(n)？

单调性/合法性让我们只做“前进”，不回退

每个元素进/出窗口至多一次

操作是 O(1) 均摊（deque/hash）

这是“策略 + 状态结构”对齐的结果：
只维护必要信息，避免全局重算。

7. 常见误区

用 heap 做“固定窗口最大值” → 多余，O(n log k) 变慢

忘记“每元素最多进出一次” → 误判复杂度

不清楚窗口要维护什么 → 状态结构选错

8. 总结（骨架句）

**Sliding Window = 局部策略（扩张/收缩）

针对窗口性质选择最小必要状态结构

把每步操作成本压到 O(1)/O(log k)，
从而把整体复杂度降到 O(n)/O(n log k)。**