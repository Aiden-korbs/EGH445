# LQR Tuning Q and R

## LQR Fundamentals Recap

**Goal**: Find $u(kT)=-Kx(kT)$ that minimises a quadratic cost function over an infinite horizon.

### Cost Function (J)

Balances state regulation (Q, state weighting) and control effort (R, control weighting):

$$J=\sum_{k=0}^{\infty}\left(x(kT)^\top Qx(kT)+u(kT)^\top Ru(kT)\right),\quad Q\succeq 0,\quad R\succ 0$$

### Solution: DARE

Solve the Discrete Algebraic Riccati Equation for a unique, positive semi-definite matrix P:

$$P=G^\top PG-(G^\top PH)(R+H^\top PH)^{-1}(H^\top PG)+Q$$

Then the gain is:

$$K=(R+H^\top PH)^{-1}H^\top PG$$

### Stability

The closed-loop system $x(kT+T)=(G-HK)x(kT)$ is guaranteed stable if **(G, H) is controllable** and **(G, V) is observable**, where Q = V^\top V.

## (G, V) Observability

- The matrix V (from Q = V^\top V) defines which states or state combinations are penalised in the cost J.
- **(G, V) observability** ensures that any unstable behaviour will eventually affect the states penalised by Q, forcing the controller to act.

### Analogy with C

| C | V |
|---|---|
| Describes outputs — what states are **measured** (through physical sensors) | Describes what states are **penalised** (design choice in Q) |
| Hardware/sensor constraint | Tuning/design parameter |
| Analogous to full state feedback assumption | V and C do not need to be the same |

## Tuning Q and R in Practice

### Starting Point: Diagonal Matrices

- Q = diag(q_1, q_2, ..., q_n): Penalises squared state deviations q_i x_i^2
- R = diag(r_1, r_2, ..., r_m): Penalises squared control inputs r_j u_j^2

### Relative Weights Matter

- The **absolute values** of Q and R don't matter as much as their **ratio**.
- Scaling both Q and R by the same factor results in the same gain K.
- Common practice: **Fix one element** (e.g., R = 1 or R = I) and tune the elements of Q.

### Interpreting Weights

- **Larger q_i** means state x_i is more important to regulate quickly / keep small.
- **Larger r_j** means control input u_j is more "expensive" (e.g., energy consumption, saturation limits).

## Tuning Strategies

### Bryson's Rule (Rule of Thumb)

Scale weights based on maximum acceptable deviations/inputs:

$$q_{ii}\approx\left(\frac{1}{\text{max acceptable }x_i}\right)^2,\quad r_{jj}\approx\left(\frac{1}{\text{max acceptable }u_j}\right)^2$$

### Trial and Error (Simulation/Experiment)

1. Simulate/run the system.
2. Observe states x(kT) and inputs u(kT).
3. If states converge too slowly $\rightarrow$ **Increase** elements in Q relative to R.
4. If control effort is too high/saturating $\rightarrow$ **Increase** elements in R relative to Q.

### Non-Diagonal Weights

- Off-diagonal terms in Q can penalise relationships between states (e.g., x_1 x_2).
- Off-diagonal terms in R can penalise simultaneous use of multiple actuators.
- Use only if there's a clear physical reason; increases tuning complexity.
