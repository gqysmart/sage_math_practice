# general notion

## Intelligent agent

An intelligent agent selects actions that maximize the **expected permance measure**, given its percepts and knowledge.

The performance measure is an external criterion used to evaluate an agent's behavior, while the utility function is an iternal representation that the agent uses to make decisions. The utility function is designed as a proxy for the permance measure, but the two are not necessarilly identical.

- Intelligence ≠ always producing the correct answer
- Intelligence  = rational action under performance
- Optimizaion is over expected performance, not guaranteed outcomes

## Task environment

## The four paradigms of agent

1. Simple reflex : Condition-action rules, no internal state
1. Model-based : Maintains an internal model of the world.(Transition model and Sensory model)
1. Goal-based : Choose actions to achieve goal states
1. Utility-based : Choose actions that maximize utility

Except for simple reflex agents,  all paradigms implicitlly relay on knowledge representation.

## State Representations

### Atomic State

- Indivisible states
- No internal structure
- large search spaces

### Factored State

- State  = a set of variables(attributes)
- Supports conditional reasoning
- Typical in MDPs

### Structured/Relational State

- Objects + relations
- Compositional and generalizable
- Typical representations:
        - First-Order-Logic(FOL)
        - Relational databases
        - Graph-based representations

Criterion for "structured"
Can we define **general rules" that apply to new objects and configurations?

## What are rules

### Essence of rules

Rules encode constraints on how states can change and how actions affect the world.
Rules may appear as:

- Inference rules
- Action schemas(preconditons & effects)
- Transiton axioms
- Constraints
- Policies

#### State representation and rules must match

| State Representation| Rule form|
|:==:|:==:|
|Atomic| if-then rules|
|Factored| Logical conditions|
|Structured| FOL/STRIPS/PDDL|

If states are structured, rules are not simple if-else statements, but logical expression with variables and quantifiers.

## learning agents and alignment

An learning agent augments a classical agent with learning mechanisms.
**Standard components**

- Performance Element - selects and executes actions
- Learning Element - Updates models(Transition models and Sensor models) or policies
- Critic - evaluates performance
- Problem generator - encourages exploration

## Do Machine learning and deep learning use rules?

### Core insight

Rules do not disappear in ML/DL;
They become implicit, parameterized functions. Formally:

```txt
    rule = f(x;theta)
```

- Rules are learned from data
- Represented as functions
- Low interpretability
- Statistical(distriutional) generalization

### Symbolic vs Neural rules

| Aspect| Symblic AI| Neural networks|
|:==:|:==:|:==:|
|Rules| Explicit|Implicit|
|Reasoning| Rule execution| Forward Pass|
|Generalization|Compositional|Statistical|
|Control|High|limited|

## Is vectorized State Representation "more structured"

### Key conclusion

Vetorized states are not strutured, nor "more relational".
They compress and dissolve structure inot geometry.

Vector embeddings:

- Can encode relations implicitly
- cannot explicitly represent relations
- Cannot support rule-based reasoning
- Cannot directly enable compositional generalization

**Vector approximate structure; they do not represent it.**

## Why do unstructured neural networks work so well?

Because they:

- Do not need interpretability
- Do not need symbolic reasoning
- Do not need explicit generalization
- Use massive data, parameters, and compute

**Neural networks aim to succeed within the training distribution, not to "understand" the world.**

## What is the human design direction?

Not :

- Fully structuing neural networks
- Returning to pure symbolic AI
But rather:

**Introduce structure only where control, reasoning, safety, or alignment is required;
Keep neural methods where perception and statistics dominate.

Contemporary neural networks do not reason;
they use large-scale statistical approximation to emulate the results of reasoning.
Structure remains indispensable wherever correctness, controllability,
generalization, and alignment are required.

#### performance element

#### learning element

#### critic

#### Problem generator



## 决策机制
## 实现