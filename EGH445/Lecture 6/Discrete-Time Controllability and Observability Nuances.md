# Discrete-Time Controllability and Observability Nuances

## Main Point
- Discrete-time controllability and observability use the **same mathematical tests** as continuous time, but the sampled model introduces some extra subtleties.

## Key Nuances
### 1. Sampling time can change the property
- A continuous-time system that is controllable or observable may lose that property after sampling, depending on the sampling period $T$.

### 2. Loss cannot be repaired by sampling
- If the **continuous-time** system is not controllable or observable, then its discrete-time version will also not be controllable or observable for any $T$.

### 3. Sampling can introduce problematic eigenvalue relationships
- The lecture notes mention a sufficient condition related to differences in continuous-time eigenvalues and the sampling frequency.
- The high-level exam takeaway is:
  - **sampling choice can matter**
  - the property is not purely inherited blindly from continuous time

## State Dimensions
For the standard discrete model:
$$
G\in\mathbb{R}^{n\times n},\quad H\in\mathbb{R}^{n\times m},\quad C\in\mathbb{R}^{p\times n},\quad D\in\mathbb{R}^{p\times m}
$$

## Design Consequence
- Before applying [[Discrete State Feedback]], always test:
  - controllability for pole placement
  - observability for state reconstruction or observer work

## Quick Comparison
| Topic | Continuous Time | Discrete Time |
|---|---|---|
| Representation | signals | sequences |
| State matrix | $A$ | $G$ |
| Control test | $\operatorname{rank}(\mathcal{C}_{AB})=n$ | $\operatorname{rank}(\mathcal{C}_{GH})=n$ |
| Observe test | $\operatorname{rank}(\mathcal{O}_{AC})=n$ | $\operatorname{rank}(\mathcal{O}_{GC})=n$ |
| Extra concern | system physics | system physics + sampling time |

## Links
- [[Controllability]]
- [[Observability]]
- [[Direct Design Approach]]
