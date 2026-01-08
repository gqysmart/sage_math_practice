# Quadratic Form Model

## WHAT

The quadratic form model represents how a vector interacts with a symmetric matrix to produce a scalar quantity.

In this model:

- Objects of interest are vectors $v \in \mathbb{R}^d$
- A symmetric matrix $A \in \mathbb{R}^{dxd}$ defines a scalar-valued function
- The interaction between v and A is expressed as quadratic form

The central object of the model is the mapping:
$$
Q(v) = v^\top A v
$$
which assigns a real number to each direction v.

---

## WHY

The quadratic form model is motivated by the need to quantify direction-dependent magnitude, energy, or variation.

key reasons for using this abstraction include:

- It provides a scalar evaluation of a vector relative to a matrix
- It naturally arises from biliear forms when both arguments coincide
- Many geometric and statistical quantities can be expressed as quadratic forms
- Optimization over directions becomes well-defined and interpretable

By reducing directional structure to scalar values, the model enables comparison, ranking, and extremization of directions.

---

## HOW

The model operates by associating each direction v with a scalar determined by the matrix A.

Formally:
$$
Q(v) = v^\top A v
$$

Key properties:

- If A is symmetric, Q(v) is real-valued for all v
- Scaling v scales Q(v) quadratically
- Restricting v to unit norm isolates directional effects

Geometrically, a quadratic form defines level sets of equal value, which correspond to ellipoids ( or degenerate cases) in $\mathbb{R}^d$.

The matrix A determines:

- The principal directions of variation
- The relative strength associated with each direction

---

## LIMITATION

The quadratic form model has explicit limitations:

- It depends entirely on second-order interactions
- Non-quadratic or higher-order effects are not captured
- Interpretability relies on symmetry of the matrix A
- Directional informaion alone may ignore contextual or structural constraints

Additionally:

- Different matrices may induce identical quadratic forms under scaling
- The model does not specify how A is obtained or estimated

As a result, the quadratic form model is most effective when directional magnitude is the primary quantity of interest.

---

## NOTES

- Quadratic forms are invariant under orthogonal change of coordinates
- Positive semi-definiteness of A ensures non-negative values
- Many optimization and spectral problems are naturally expressed
  in terms of quadratic forms
  