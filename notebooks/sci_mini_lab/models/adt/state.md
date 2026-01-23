# ADT Note: State — Full ADT Specification

> **State ADT** 描述的是系统在任一时刻的**可观察配置（configuration as value）**，
> 而不是对象身份或执行过程。

---

## 0. 语义前提（Semantic Assumptions）

* **State 是值（value），不是对象（object）**
* **状态改变在语义上表现为返回新值**：

```
transition : State × Action → State
```

* 实现层可以使用 mutable 优化，但**语义上必须等价于返回新 state**

---

## 1. Value Domain（值是什么）

### 定义

> **State 的值域，是系统所有“合法配置”的集合。**

直观表达：

```
State ≈ { (v1 = x1, v2 = x2, ..., vn = xn) | constraints }
```

### 语义要点

* State 是一个“快照”，而非运行过程
* State 必须是可比较、可替换的
* 所有合法 State 构成一个**状态空间**

---

## 2. Operations（允许做什么）

### 2.1 Observers（观察操作）

> **不改变 state，仅用于读取或判断**

```
get        : State × Key → Value
isValid    : State → Bool
isTerminal : State → Bool
summary    : State → Description
```

语义约束：

* 观察结果只依赖 state 的值
* 不依赖历史、路径或身份

---

### 2.2 Transformers（状态变换操作）

> **返回新的 state（语义层）**

```
init        : → State
transition  : State × Action → State
update      : State × Delta → State
```

语义说明：

* 每次变换产生新的 state 值
* 旧 state 在语义上不可再被观察

---

## 3. Illegal Operations（什么不允许）

### 3.1 非法操作输入

* 对终止状态执行 transition
* 使用不属于 AllowedActions(s) 的 action
* 访问不存在的 key

### 3.2 非法状态构造

* 绕过 init / transition 直接拼装 state
* 构造违反 invariant 的配置

### 3.3 语义禁止行为

* 比较 state 的对象身份
* 依赖创建顺序或内存位置
* 通过副作用跨 state 传播信息

---

## 4. Invariants（永远成立的）

> **Invariant = 对所有合法 state 都必须成立的断言**。
> 若违反 invariant，该配置不属于 State 值域。

### 4.1 Structural Invariants（结构不变量）

```
∀ s ∈ State:
  s has fields {f1, f2, ..., fn}
  ∧ type(f_i(s)) ∈ AllowedType_i
```

* 必需字段存在
* 类型/范围合法

---

### 4.2 Domain / Constraint Invariants（领域约束）

```
∀ s ∈ State:
  C1(s) ∧ C2(s) ∧ ... ∧ Ck(s)
```

* 资源 ≥ 0
* 概率和 = 1
* 权限/边界不越界

---

### 4.3 Transition Preservation（演化保持性）

```
∀ s ∈ State, ∀ a ∈ AllowedActions(s):
  Invariant(s) ⇒ Invariant(transition(s, a))
```

> 若某操作可能破坏 invariant，
> 则该操作不属于 ADT。

---

### 4.4 Observational Consistency（观察一致性）

```
s1 ≈ s2  ⇔  ∀ observer o, o(s1) = o(s2)
```

* 支持商空间
* 支持状态压缩 / 哈希
* 支持良定义性

---

### 4.5 Semantic Safety（语义安全）

```
∀ s ∈ State:
  ¬Bad1(s) ∧ ¬Bad2(s) ∧ ...
```

* 不存在非法但可达状态
* 不存在系统级灾难状态

---

## 5. Equivalence（什么时候算同一个）

### 定义（外延等价）

> **两个 state 等价，当且仅当系统无法区分它们。**

```
s1 ≈ s2  ⇔
  ∀ observer o, o(s1) = o(s2)
```

### 语义后果

* 等价类形成商空间
* 决策/策略只依赖等价类

---

## 6. ADT 完整总结

```
ADT State

Value Domain:
  All valid system configurations

Operations:
  Observers: get, isValid, isTerminal
  Transformers: init, transition

Illegal:
  Invalid actions
  Invalid construction
  Identity-based reasoning

Invariants:
  Structural
  Domain constraints
  Preservation
  Observational consistency
  Semantic safety

Equivalence:
  Observational equivalence
```

---

## 7. 关键结论

> **State ADT 的核心作用，
> 是定义“什么时候两个世界是同一个世界”。**

> 一旦 State 被严格定义，
> 决策、搜索、RL、建模问题
> 都自然落在其上。
