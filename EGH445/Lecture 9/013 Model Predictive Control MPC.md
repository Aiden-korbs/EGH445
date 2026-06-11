# Model Predictive Control (MPC)

## Overview

**Model Predictive Control (MPC)** is a powerful control strategy that uses an optimisation problem to determine the control input at each time step. It is particularly useful for systems with constraints and nonlinearities.

## Core Concept

While LQR solves the **infinite-horizon** optimal control problem, MPC solves a **finite-horizon** optimisation problem at each time step.

The finite horizon used by MPC is called the **prediction horizon** — how many steps ahead the controller looks.

## How MPC Works

MPC follows a receding-horizon strategy:

1. **Optimise:** Find an optimal control sequence $[u(kT), u(kT+T), \dots, u(kT + (N-1)T)]$ for a finite prediction horizon of $N$ steps, subject to system dynamics and constraints
2. **Apply:** Apply only the first control input $u(kT)$ to the system
3. **Receding:** At the next time step $kT + T$, use the current state as the new initial condition and re-solve the optimisation problem

This repeated re-optimisation at each step is called the **receding horizon** (or receding control horizon) principle.

## MPC vs LQR Comparison

| Aspect | LQR | MPC |
|---|---|---|
| Horizon | Infinite | Finite (prediction horizon $N$) |
| Constraints | Not handled | Explicitly handles constraints |
| Computation | Offline gain, online: $u = -Kx$ | Online optimisation at each step |
| Complexity | Low | Higher |
| Constraints | No (saturation breaks guarantees) | Yes (input, state, rate limits) |
| Nonlinear systems | Linearised model only | Can use nonlinear models |
| Optimal solution | Unique, analytical | Numerical, per step |

## MPC Advantages

- **Handles constraints naturally:** Input limits, state limits, rate-of-change limits are all incorporated as inequality constraints in the optimisation
- **Flexible:** The cost function and constraints can be changed online
- **Multi-variable:** Handles MIMO systems without additional complexity
- **Performance:** Can achieve better performance near constraint boundaries than saturated LQR

## MPC Disadvantages

- **Computational cost:** Requires solving an optimisation problem at each time step
- **Model dependency:** Performance depends on the accuracy of the system model
- **Implementation complexity:** Requires an optimisation solver (e.g., QP solver, CVXPY)
- **Tuning:** Requires choosing a prediction horizon $N$ in addition to cost weights

## MPC Formulation

At each time step $k$, MPC solves:

$$\min_{u(k), \dots, u(k+N-1)} \sum_{j=0}^{N-1} \left( x(k+j)^\top Q x(k+j) + u(k+j)^\top R u(k+j) \right)$$

subject to:

- System dynamics: $x(k+j+1) = G x(k+j) + H u(k+j)$
- Input constraints: $u_{\min} \leq u(k+j) \leq u_{\max}$
- State constraints (optional): $x_{\min} \leq x(k+j) \leq x_{\max}$
- Initial condition: $x(k) = x_{\text{current}}$

Only $u(k)$ is applied; the horizon recedes to the next step.

## Key Takeaways

- MPC uses finite-horizon optimisation with receding horizon strategy
- Explicitly handles constraints (input limits, state limits, rate limits)
- More computationally intensive than LQR but more flexible
- Best suited for constrained systems where saturated LQR would fail

## Related

- [[012 LQR Limitations and Control Saturation]]
- [[006 Optimal Control Fundamentals]]
- [[007 Discrete Linear Quadratic Regulator DLQR]]
