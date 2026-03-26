# Discrete Transfer Function from Continuous Models

## Key Idea
- To derive a discrete transfer function from a continuous plant, the **Zero-Order Hold** must be included.
- Sampling alone is not enough.

## Important Warning
- These are **not equivalent**:
  - sampling the plant directly
  - modelling the held input through a ZOH before the plant

## Zero-Order Hold
- The Laplace-domain transfer function of the ZOH is:
$$
G_{\text{ZOH}}(s) = \frac{1 - e^{-Ts}}{s}
$$

## Correct Continuous-to-Discrete Modelling Block
$$
G_{\text{ZOH}}(s)G(s)
$$

## Discrete Transfer Function Formula
$$
F(z) = \mathcal{Z}\left\{G_{\text{ZOH}}(s)G(s)\right\}
$$

## Equivalent Form
Using
$$
G_{\text{ZOH}}(s) = \frac{1-e^{-Ts}}{s}
$$
gives:
$$
F(z) = \mathcal{Z}\left\{\frac{1-e^{-Ts}}{s}G(s)\right\}
$$

Using $z^{-1} = e^{-Ts}$:
$$
F(z) = (1-z^{-1})\mathcal{Z}\left\{\frac{G(s)}{s}\right\}
$$

## Why the ZOH Matters
- The plant input is held constant between samples.
- The discrete model must reflect that held input to match the real digital control architecture.

## Links
- [[Z Transform]]
- [[Pulse Transfer Functions]]
- [[Discrete-Time System Response]]

## Visuals
![[ZOH Before Plant.png|400]]
![[Incorrect vs Correct Discretisation.png|400]]
