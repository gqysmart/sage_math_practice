# Decision Problems

A dicision problem consists in choosing acitons sequentially in different states of environment in order to achieve a goal or maximize long-term reward.

Core elements:

- State space S
- Action space A
- State transitions (deterministic or probabilistic)
- Goal or reward function

**This abstraction underlies search, planning, MDPs, and reinforcement learning.

## Action Sequence

An action sequence is a fixed, ordered list of actions $[a_1,a_2,...,a_n]$

### Key properties

- Independent of feedback during execution
- Valid for a specific instances of the world
- Assumes a deterministic environment

### Typical use cases

- State-space search(BFS,$A^*$)
- Classical planning(STRIPS)

**An action sequence is *not a general solution*, but a solution for one deterministic instance**.

## Policy

A policy is a mapping from states to actions, specifying what action to take in each possible state.
Forms:

- Deterministic policy: $\pi(s)= a$
- Stochastic policy: $\pi(a|s) $

A policy is not necessarily probabilistic, the essence of a policy is ***State-dependent(conditional) descision-making***

## Searching, Planning, vs Decision problems

### Search

Find a path from an initial state to a goal state
Solution: a path/action sequence

### Planning

- Use explicit action models(preconditons + effects)
- Combines search with logical inference
- Solution: a plan (action sequence)

Planning is best viewed as **structured search with semantics**

### Decision Problems(MDP/RL)

- Environment may be stochastic
- Action outcomes are uncertain
- The agent must act in all states
- Solution : a policy



