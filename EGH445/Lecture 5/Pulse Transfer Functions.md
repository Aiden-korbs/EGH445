# Pulse Transfer Functions

## Definition
- A **pulse transfer function** is the discrete-time equivalent of a continuous-time transfer function.
- It relates the $\mathcal{Z}$ transforms of sampled input and output signals.

## Basic Form
$$
F(z) = \frac{Y(z)}{X(z)}
$$

## Role
- Pulse transfer functions let us analyse:
  - open-loop dynamics
  - closed-loop dynamics
  - characteristic equations
  - stability
  - response

## Closed-Loop Forms
### Synchronous sampled input and output
$$
F_c(z) = \frac{F(z)}{1 + F(z)H(z)}
$$

### Sampled input with unsampled output path representation
$$
F_c(z) = \frac{F(z)}{1 + F H(z)}
$$

## Characteristic Equation
- The closed-loop characteristic equation is obtained from the denominator:
$$
1 + F(z)H(z) = 0
$$
or in the alternative representation:
$$
1 + F H(z) = 0
$$

## Key Idea
- Pulse transfer functions play the same role in discrete time that ordinary transfer functions play in continuous time.

## Links
- [[Z Transform]]
- [[Discrete Transfer Function from Continuous Models]]
- [[Discrete Transfer Function from State Space]]
- [[Discrete-Time Stability]]

## Visuals
![[Pulse Transfer Function Closed Loop.png|400]]
