← Back to [[Week 2 Workshop - System Response and Stability]]

# Numerical Integration

## Core Idea
- For nonlinear systems, the [[ODE General Solution]] integral must be solved **iteratively** from the initial condition.
- This process is called **numerical simulation**.

## Discrete Time Instances

$$t_n = t_0 + nh, \quad n = 0, 1, 2, \ldots, N$$

- $h$ is the **integration step size** (smaller $h$ = more accuracy, more computation).

## Iterative Update Rule

$$x(t_0) = x_0$$

$$x(t_{n+1}) = x(t_n) + \int_{t_n}^{t_{n+1}} f(x, u) \, dt$$

- $x(t_n)$ → **current** state (current step/time)
- $x(t_{n+1})$ → **next** state (next step/time)
- The integral captures the **motion** over the time window given the dynamics $f$ and input $u$.

## Integration Methods

| Method | Notes |
| :--- | :--- |
| **Euler (Forward)** | Simple, first-order accuracy |
| **Euler (Backward)** | Implicit, more stable |
| **Heun-Euler (Trapezoidal)** | Second-order accuracy |
| **MATLAB ODE Solvers** | Variable-step, suited to stiff systems |

- MATLAB and Simulink offer a variety of ODE solvers (e.g. `ode45`, `ode15s`) for different system types.

![[Numerical Integration Step Diagram.png|400]]

## MATLAB Reference
- See Canvas: `Numerical_Integrations.m`

## Related Notes
- [[ODE General Solution]]
- [[Analytical Solution - Linear Systems]]
