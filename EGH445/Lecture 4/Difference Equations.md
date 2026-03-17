← Back to [[Discrete-time Control System Modelling]]

# Difference Equations

## What are Difference Equations?
- Describe a system (plant or controller) in **discrete time** — relating past and present sampled inputs and outputs.
- Are **approximations** to continuous-time differential equations.
- Relate state changes with respect to **finite changes in time** (the sampling period $T$), rather than infinitesimal changes.
- Are **recursive** — computers must use difference equations, not differential equations, for calculations.

## Continuous vs Discrete System Representations

| Domain | Representations |
| :--- | :--- |
| **Continuous time** | Differential equation → Continuous state space → Continuous transfer function |
| **Discrete time** | Difference equation → Discrete state space → Discrete transfer function |

## The Discrete Derivative

The continuous derivative is defined as:

$$\dot{x}(t) = \lim_{\Delta t \to 0} \frac{x(t + \Delta t) - x(t)}{\Delta t} \quad \text{(infinitesimal time)}$$

For discrete time, we **approximate** the derivative at each sample time:

$$\dot{x}(kT) \approx \frac{x(kT + T) - x(kT)}{T} \quad \text{(finite time)}$$

This is a **first-order approximation** (1st order Taylor series) to the derivative at $t = kT$.

> This approximation is the **Euler Forward method**. Other approximations (Euler Backward, trapezoidal) are also possible since this is essentially numerical integration — see [[Numerical Integration]].

## Deriving Difference Equations from Differential Equations

**Scenario:** Derive difference equations for a mass-spring-damper system.

**Given** continuous state space:

$$\dot{x}(t) = \begin{bmatrix} 0 & 1 \\ a & b \end{bmatrix} x(t) + \begin{bmatrix} 0 \\ c \end{bmatrix} u(t)$$

**Steps:**

Apply the discrete derivative approximation to each equation:

$$\frac{x_1(kT+T) - x_1(kT)}{T} \approx x_2(kT)$$

$$\boxed{x_1(kT+T) \approx x_1(kT) + Tx_2(kT)}$$

$$\frac{x_2(kT+T) - x_2(kT)}{T} \approx ax_1(kT) + bx_2(kT) + cu(kT)$$

$$\boxed{x_2(kT+T) \approx Tax_1(kT) + (1 + Tb)x_2(kT) + Tcu(kT)}$$

**Final Notes:**
- These two first-order difference equations can be written in **discrete state space form**:

$$x(kT+T) = Gx(kT) + Hu(kT)$$
$$y(kT) = Cx(kT) + Du(kT)$$

- As $T \to 0$, the system approaches the continuous-time system ($x(kT+T) \to x(kT)$).
- The approximation is only valid when $T$ is **very small**. For larger $T$, use [[Discrete State Space Models - Overview|exact approximations]].
- For 2nd order systems, difference equations may contain terms in $x(kT + 2T)$ or $x(kT - 2T)$ depending on the derivative approximation used.

## Related Notes
- [[Discrete State Space Models - Overview]]
- [[Finding the G Matrix]]
- [[Finding the H Matrix]]
- [[Numerical Integration]]
