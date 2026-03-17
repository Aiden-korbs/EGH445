← Back to [[Week 2 Workshop - System Response and Stability]]

# ODE General Solution

## Core Idea
- Given a dynamical system, we want to **understand how it behaves** for $t \geq t_0$.
- This means "solving" the system: given an input, initial condition, and model — what are the outputs and state changes?

## General System Form

$$\dot{x} = f(x, u)$$

- Subject to input $u(t)$ and initial condition $x(t_0) = x_0$.

## General Solution

$$x(t) = x(t_0) + \int_{t_0}^{t} f(x, u) \, dt$$

- Because of this integral, solving an ODE is called **ODE integration**.
- **Analogy:** Finding distance by integrating velocity over time from a known start position.

## Linear vs Nonlinear

| System Type | Solution Method |
| :--- | :--- |
| **Linear** | Analytical formulas exist |
| **Nonlinear** | Integral solved numerically (simulation) |

## Related Notes
- [[Numerical Integration]]
- [[Analytical Solution - Linear Systems]]
