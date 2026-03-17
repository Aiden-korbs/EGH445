← Back to [[Week 2 Workshop - System Response and Stability]]

# Analytical Solution — Linear Systems

## System Form

$$\dot{\mathbf{x}} = A\mathbf{x} + B\mathbf{u}$$

Subject to input $u(t)$ and initial condition $\mathbf{x}(t_0) = \mathbf{x}_0$.

## General Analytical Solution

$$\boxed{x(t) = e^{At}x_0 + \int_0^t e^{A(t-\tau)} B u(\tau) \, d\tau}$$

| Term | Name |
| :--- | :--- |
| $e^{At} x_0$ | **Homogeneous** solution ($\dot{x} = Ax$, no input) |
| $\int_0^t e^{A(t-\tau)} B u(\tau) \, d\tau$ | **Particular** solution (forced response) |

## Homogeneous (Autonomous) Solution

The case with **no input** $u(t) = 0$:

- **Scalar** (1 state): $\dot{x} = ax$, $x(0) = x_0 \Rightarrow x = e^{at} x_0$
- **Vector** (>1 state): $\dot{\mathbf{x}} = A\mathbf{x}$, $\mathbf{x}(0) = \mathbf{x}_0 \Rightarrow \mathbf{x} = e^{At}\mathbf{x}_0$

> Sometimes called the **autonomous** solution.

## Proof Sketch
Assume $x(t) = e^{At}x_0$ is the solution → differentiate $x(t)$ → simplify using [[State Transition Matrix]] properties → integrate → add initial conditions.

## Related Notes
- [[ODE General Solution]]
- [[State Transition Matrix]]
- [[Internal Stability]]
