← Back to [[Discrete-time Control System Modelling]]

# Discrete State Space Models — Overview

## Motivation
[[Difference Equations]] derived via the discrete derivative provide only **numerical approximations** to the continuous-time system — valid only for small $T$.

Ideally, we want an **exact representation** of the continuous-time system at the sampling instances $\{kT,\; kT+T,\; kT+2T,\; \ldots\}$ so that larger (slower) sampling times can be used.

## Approximation Pathways

| Approach | Path | Notes |
| :--- | :--- | :--- |
| **Numerical** | Continuous SS → Differential Eqn → Difference Eqn → Approx Discrete SS | Requires small $T$ |
| **Exact** | Continuous SS → Exact Discrete SS | Valid at sampling instances for any $T$ |

## Discrete Time State Space Model

For a **linear system**, the exact discrete-time state space model is:

$$\boxed{x(kT+T) = Gx(kT) + Hu(kT)}$$

$$\boxed{y(kT) = Cx(kT) + Du(kT)}$$

## Matrix Relationships: Continuous → Discrete

| Continuous | Discrete | Notes |
| :--- | :--- | :--- |
| $A$ | $G = e^{AT}$ | State/transition matrix |
| $B$ | $H = \int_0^T e^{A\lambda} d\lambda\, B$ | Input matrix |
| $C$ | $C$ | Unchanged |
| $D$ | $D$ | Unchanged |

## Derivation Summary (4 Steps)

**Step 1 — Continuous-time solution:**

$$x(t) = e^{At}x(t_0) + \int_0^t e^{A(t-\tau)} Bu(\tau)\,d\tau$$

**Step 2 — Evaluate at $t = kT$ and $t = kT+T$**, then subtract to express $x(kT+T)$ in terms of $x(kT)$.

**Step 3 — Assume ZOH** (constant input over sampling period):

$$u(\tau) = u(kT), \quad \tau \in [kT,\; kT+T)$$

This allows $B$ and $u(kT)$ to be taken outside the integral.

**Step 4 — Change variable** $\lambda = kT + T - \tau$ to simplify limits, yielding:

$$x(kT+T) = \underbrace{e^{AT}}_{G} x(kT) + \underbrace{\left(\int_0^T e^{A\lambda}d\lambda\right)B}_{H} u(kT)$$

## Important Points

- The model is **exact at the sampling instances** because it uses the analytical continuous-time solution.
- The ZOH assumption (constant input per interval) is **physically valid** for real digital control systems.
- The choice of sampling time $T$ directly affects $G$ and $H$ — a stable continuous-time system **may become unstable** for certain values of $T$.
- As $T \ll 1$: $G \approx e^{A \cdot 0} = I$ — the next state is just the last state plus $Hu(kT)$.
- $G$ and $H$ are sometimes written $G(T)$ and $H(T)$ to emphasise their dependence on sampling time.

> Do not confuse $G$ and $H$ here with transfer function notation.

## Related Notes
- [[Difference Equations]]
- [[Finding the G Matrix]]
- [[Finding the H Matrix]]
- [[Sampling Time and Frequency Selection]]
- [[Zero Order Hold and Data Hold]]
- [[Analytical Solution - Linear Systems]]
