# State vs Output Feedback

## System Matrices: G, H, C Interpretation

For the discrete-time system:

$$x(kT+T)=Gx(kT)+Hu(kT),\quad y(kT)=Cx(kT)$$

- **G = e^{AT}** — Represents internal dynamics of the system; describes how x(kT) evolves over time. Inherent to the system.
- **H = \int_0^T e^{A\tau}Bd\tau** — Represents how the input u(kT) affects the state x(kT). Relates to the actuators chosen (motors, heaters, valves, etc.).
- **C** — Represents how states are measured as outputs y(kT). Relates to sensors chosen (types and placement of sensors, cameras, etc.).

## State Feedback vs Output Feedback Comparison

| Aspect | State Feedback: $u(kT)=-Kx(kT)$ | Output Feedback: $u(kT)=-K\hat{x}(kT)$ |
|---|---|---|
| Requirement | System (G, H) must be **controllable** | System (G, C) must be **observable** |
| Closed-loop dynamics | $G_{cl}=G-HK$ | Observer dynamics: $G_{obs}=G-LC$ |
| Assumption | Assumes all states are available | Used when only y(kT)=Cx(kT) is available |
| Gain design | Pole placement: K gain; LQR: K from Q, R; Integral action: dynamic extension + K_I | Luenberger Observer: L gain; Kalman Filter: K_k and noise covariances Q, R |
| What is measured | Nothing assumed — full state available | y(kT) is what is actually measured; need to estimate $\hat{x}(kT)$ from y(kT) and u(kT) |

## Practical Question: Measure vs Estimate

When is it feasible/necessary to measure all states versus estimate them?

- **Sensor cost and complexity** — relates to choice of C
- **Sensor availability** — some states might be internal/unmeasurable
