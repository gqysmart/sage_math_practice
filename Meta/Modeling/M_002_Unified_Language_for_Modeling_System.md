# M_002 · Unified Language for Modeling Systems

> **Type**: System Model (not Mathematical Model)
>
> **Purpose**: Provide a single, reusable modeling language to understand, design, and evolve complex systems across domains (OOP, AI Pipelines, Synthetic Data, UnrealCV, Web/API).

---

## 0. Positioning (Why this exists)

* **Mathematical models** describe *local laws* (functions, distributions, optimization).
* **System models** organize *global complexity* (roles, states, data flow, boundaries, failure isolation).

This document defines a **system modeling language** that sits *above* math models and *guides where and how* they are used.

---

## 1. Core Principle

> **Same language, different scales.**
>
> The same modeling vocabulary applies to:
>
> * Object-level systems (OOP)
> * Pipeline-level systems (AI training/evaluation)
> * World-to-data systems (Synthetic Data / Simulation)

Only the **scale** changes—not the language.

---

## 2. The Minimal Syntax (6 Questions)

For any system, answer **only** these six questions:

1. **System** — What system am I modeling?
2. **Roles / Entities** — Who has responsibility?
3. **State** — What defines the system at a moment in time?
4. **Behavior / Transform** — How does state change?
5. **Boundary / Contract** — How does the system interact with the outside?
6. **Failure / Invariant** — Where can it break, and how is failure isolated?

This is the *minimal grammar* of the language.

---

## 3. Primitive Concepts (Vocabulary)

### 3.1 Role / Entity

* A **responsibility holder**, not an implementation.
* Stable over time.

Examples:

* OOP: Controller, Service, Repository
* AI: Dataset, Model, Trainer, Evaluator
* Synthetic Data: Scene, Camera, Sensor, Labeler

---

### 3.2 State

* Explicit, inspectable representation of "what is".
* Prefer **explicit data structures** over implicit variables.

Examples:

* Object attributes
* Model weights / hyperparameters
* World state, camera pose

---

### 3.3 Behavior / Transform

* Operations that map **state → state** or **state → output**.
* Prefer **pure transforms** when possible.

Examples:

* method calls
* train / infer / render
* step(world) → world'

---

### 3.4 Boundary / Contract

* Where the system meets the outside world.
* Defined by **schemas**, not logic.

Examples:

* API endpoints
* Pydantic schemas / DTOs
* Image + label formats

---

### 3.5 Failure / Invariant

* Expected breakpoints.
* Enforced invariants define correctness.

Examples:

* Validation errors
* Shape / coordinate mismatches
* Sync failures

---

## 4. Mapping to Code (Implementation Guidance)

### 4.1 Role → Module / Component

* One role = one stable module (class, package, service).
* Implementation choice is secondary.

### 4.2 State → Explicit Data Objects

* Use dataclasses / typed structs.
* Avoid scattered implicit state.

### 4.3 Behavior → Transform Functions

* Prefer functions with explicit inputs/outputs.
* Side effects only at boundaries.

### 4.4 Boundary → Schemas

* Use Pydantic / typed contracts.
* Validate early, fail fast.

### 4.5 Failure → Boundary-Level Checks

* Errors should appear where contracts are enforced.
* Core logic remains clean.

---

## 5. Same Language, Three Scales

### 5.1 Object Scale (OOP)

```
Role      → class
State     → attributes
Behavior  → methods
Boundary  → public API
Failure   → exceptions
```

### 5.2 Pipeline Scale (AI Systems)

```
Role      → dataset / model / trainer
State     → params / weights
Behavior  → fit / evaluate
Boundary  → data schema
Failure   → validation / metrics
```

### 5.3 System Scale (Synthetic Data / Simulation)

```
Role      → world / sensor / agent
State     → world state
Behavior  → step / render
Boundary  → image + label
Failure   → sync / coordinate errors
```

---

## 6. Relationship to Mathematical Models

* Mathematical models live **inside** behaviors.
* System models decide:

  * *Where* math is applied
  * *How* it is composed
  * *How* failures are isolated

> **Math explains local truth; systems manage global complexity.**

---

## 7. What This Is NOT

* Not UML
* Not a framework
* Not a diagramming tool

It is a **thinking language**—a reusable mental grammar for system design.

---

## 8. Practical Use

* Project design
* Architecture discussions
* Documentation
* Interviews / portfolios

> If you can explain a system using this language, you understand it.

---

## 9. One-Line Summary

> **A unified system modeling language built from roles, state, transforms, boundaries, and failures—independent of domain and scale.**
