# LeetCode 面试求生 Heuristics（讨巧速用版）

目标：  
- 不是深入理解算法  
- 而是**面试脑子宕机时也能推出可写解法**  
- 快速从暴力 → O(n) 优化  

---

# 一、面试第一反应（3 秒判断）

看到题先问四件事：

1. 是否判断“是否存在 / 是否重复”
   → set

2. 是否需要“key → value 映射”
   → dict

3. 是否涉及“连续区间 / substring / subarray”
   → sliding window

4. 是否“数组已排序”
   → two pointers

覆盖 LeetCode 高频题 70%+

---

# 二、脑子宕机救命流程（暴力 → 优化）

## Step 1：先写暴力

for i:
for j:


O(n²)

面试官不会扣分。

---

## Step 2：问自己

第二层循环在干嘛？

通常只有三种情况：

- 找某个值
- 找某个关系
- 扫描一个区间

---

## Step 3：替换第二层循环

### 情况 A：找值

seen = set()

for x in nums:
if x in seen:
return ...
seen.add(x)


O(n)

---

### 情况 B：找 pair / complement

map = {}

for i, x in enumerate(nums):
if target-x in map:
return ...
map[x] = i


---

### 情况 C：找区间

left = 0

for right in range(n):
while 不满足条件:
left += 1


sliding window

---

### 情况 D：找“更大/更小”

stack = []

for x:
while stack and stack[-1] < x:
stack.pop()
stack.append(x)


monotonic stack

---

# 三、O(n) 常用模板库（直接套）

## 模板 1：重复 / 出现

seen = set()
for x in nums:
if x in seen:
return True
seen.add(x)


---

## 模板 2：Two Sum

map = {}

for i, x in enumerate(nums):
if target-x in map:
return ...
map[x] = i


---

## 模板 3：最长不重复子串

window = set()
left = 0

for right in range(len(s)):
while s[right] in window:
window.remove(s[left])
left += 1
window.add(s[right])


---

## 模板 4：Prefix Sum

prefix = 0
map = {0:1}

for x in nums:
prefix += x
if prefix-k in map:
...
map[prefix] += 1


---

## 模板 5：Next Greater Element

stack = []

for x in nums:
while stack and stack[-1] < x:
stack.pop()
stack.append(x)


---

# 四、题型 → 解法速查（最关键）

| 题目关键词 | 默认解法 |
|---|---|
| duplicate / exists | set |
| pair / two sum | dict |
| longest substring | sliding window |
| sorted array | two pointers |
| next greater | monotonic stack |
| subarray sum | prefix sum |
| frequency | dict |
| top k | heap |
| interval | sort + merge |
| graph | BFS / DFS |

---

# 五、最强 heuristics（面试通用）

## Heuristic 1

题目：

- unordered
- 要 O(n)

→ 默认 hash

---

## Heuristic 2

题目：

- longest
- substring
- window

→ sliding window

---

## Heuristic 3

题目：

- sorted

→ two pointers

---

## Heuristic 4

题目：

- next greater
- temperature
- histogram

→ monotonic stack

---

## Heuristic 5

题目：

- sum
- k
- subarray

→ prefix sum

---

# 六、复杂度优化本质（记住这句）

所有 O(n) 优化，本质只有两种手段：

## 手段 A：记忆（hash）

避免重复查找

## 手段 B：移动边界（two pointers / window）

避免重复遍历

---

# 七、面试真实评分逻辑

面试官看的不是你“会不会算法”。

他们看：

1. 能否写暴力
2. 能否发现重复计算
3. 能否用数据结构降复杂度

流程：

暴力 O(n²)
→ 发现重复查找
→ 用 hash
→ O(n)


直接加分。

---

# 八、卡住时写这 5 行

暴力能不能写？

第二层循环在干嘛？

能不能用 hash 替换？

能不能用双指针？

能不能用 window？


一定能推出一个解。

---

# 九、真正的面试套路总结

算法不是“想出来的”。

而是：

> 识别题型 → 套状态结构 → 写模板

核心公式：

问题结构 → 数据结构 → 算法


而不是：

直接想算法


---

# 十、一句话版本（面试时脑内自言自语）

要存在？ set
要映射？ dict
要区间？ window
已排序？ 双指针
要 next？ 栈
要累计？ prefix

