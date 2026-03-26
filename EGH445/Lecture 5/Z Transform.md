# Z Transform

## Definition
- The **$\mathcal{Z}$ transform** is the discrete-time counterpart to the Laplace transform.
- It is used to represent sampled signals in the complex domain.

## Sampled Signal
- A sampled signal can be written as:
$$
x^*(t) = \sum_{k=0}^{\infty} x[k]\delta(t-kT)
$$

## Laplace Transform of the Sampled Signal
$$
X^*(s) = \sum_{k=0}^{\infty} x[k]e^{-kTs}
$$

## Change of Variable
- Let:
$$
z = e^{sT}
$$
so that
$$
z^{-1} = e^{-sT}
$$
and
$$
s = \frac{1}{T}\ln(z)
$$

## Unilateral Z Transform
$$
X(z) = \sum_{k=0}^{\infty} x[k]z^{-k}
$$

## Interpretation
- The $\mathcal{Z}$ transform is effectively the Laplace transform of the sampled signal under the mapping:
$$
s \leftrightarrow z = e^{sT}
$$

## Important Notes
- The version used here is the **unilateral** $\mathcal{Z}$ transform.
- This is appropriate when signals are assumed zero for negative time indices.

## Why It Matters
- The $\mathcal{Z}$ transform allows:
  - discrete transfer function derivation
  - difference-equation analysis
  - pole-zero stability analysis
  - system response calculations

## Links
- [[Pulse Transfer Functions]]
- [[Discrete Transfer Function from Continuous Models]]
- [[Discrete Transfer Function from State Space]]
- [[s-Plane to z-Plane Mapping]]

## Visuals
![[Z Transform Derivation.png|400]]
