# Discrete-Time Stability

## Core Criterion
- In discrete time, stability is determined by **pole locations in the $z$-plane**.
- The poles can be found from:
  - the characteristic equation of the transfer function
  - the eigenvalues of the state matrix $G$

## Stability Test
- A discrete-time system is **asymptotically stable** if all poles satisfy:
$$
|z_i| < 1
$$

## Categories
| Pole Location | Stability Meaning |
|---|---|
| $|z_i| < 1$ for all poles | **Stable** |
| poles on $|z|=1$ with no unstable growth case | **Marginally stable** |
| any pole with $|z_i| > 1$ | **Unstable** |

## Characteristic Equations
### From transfer function
- For a closed-loop system, solve:
$$
1 + F(z)H(z) = 0
$$

### From state-space model
- Solve:
$$
\det(zI-G) = 0
$$

## Comparison with Continuous Time
| Domain | Stability Region |
|---|---|
| Continuous time | Left-half of the $s$-plane |
| Discrete time | Inside the unit circle in the $z$-plane |

## Why It Works
- Since discrete responses contain terms like $z^k$, stability requires those terms to decay as $k \to \infty$.
- That only happens when:
$$
|z| < 1
$$

## Practical Workflow
1. Find the discrete model.
2. Form the characteristic equation.
3. Compute poles.
4. Check whether every pole lies inside the unit circle.

## Links
- [[Pulse Transfer Functions]]
- [[Discrete Transfer Function from State Space]]
- [[s-Plane to z-Plane Mapping]]
- [[Discrete Final Value]]

## Visuals
![[Discrete Stability Unit Circle.png|400]]
