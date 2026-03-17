← Back to [[Week 2 Workshop - System Response and Stability]]

# Hodgkin-Huxley Neuron Model

## Overview
- Running Example 2 for EGH445 Workshop Week 2.
- A **biological nonlinear system** modelling **neuronal membrane potential** (action potential / "firing").
- Linearised about equilibrium $\bar{x}$ using MATLAB's Model Lineariser: $\tilde{x} = A\tilde{x} + B\tilde{u}$.

![[Hodgkin-Huxley Neuron Circuit Diagram.png|400]]

## State Variables

$$x = \begin{bmatrix} V_m \\ n \\ m \\ h \end{bmatrix}$$

| Symbol | Description |
| :--- | :--- |
| $V_m$ | Membrane potential |
| $n$ | Potassium channel activation gating variable |
| $m$ | Sodium channel activation gating variable |
| $h$ | Sodium channel inactivation gating variable |

## Nonlinear Model Equations

$$I = C\dot{V}_m + G_K n^4 (V_m - E_K) + G_{Na} m^3 h (V_m - E_{Na}) + G_l (V_m - E_l)$$

$$\dot{n} = \alpha_n(V_m)(1 - n) - \beta_n(V_m) n$$

$$\dot{m} = \alpha_m(V_m)(1 - m) - \beta_m(V_m) m$$

$$\dot{h} = \alpha_h(V_m)(1 - h) - \beta_h(V_m) h$$

## Rate Functions $\alpha_x$ and $\beta_x$

| Function | Expression |
| :--- | :--- |
| $\alpha_n(V_m)$ | $\dfrac{0.01(10 - V_m)}{\exp\!\left(\frac{10 - V_m}{10}\right) - 1}$ |
| $\beta_n(V_m)$ | $0.125 \exp\!\left(-\dfrac{V_m}{80}\right)$ |
| $\alpha_m(V_m)$ | $\dfrac{0.1(25 - V_m)}{\exp\!\left(\frac{25 - V_m}{10}\right) - 1}$ |
| $\beta_m(V_m)$ | $4 \exp\!\left(-\dfrac{V_m}{18}\right)$ |
| $\alpha_h(V_m)$ | $0.07 \exp\!\left(-\dfrac{V_m}{20}\right)$ |
| $\beta_h(V_m)$ | $\dfrac{1}{\exp\!\left(\frac{30 - V_m}{10}\right) + 1}$ |

## Linearised Dynamics Matrix

$$A = \begin{bmatrix} -0.1174 & 0 & 0 & -0.0041 \\ 0 & -4.223 & 0 & 0.0264 \\ 0 & 0 & -0.1832 & 0.0028 \\ 2.0469 & 69.1512 & -55.4024 & -0.6773 \end{bmatrix}$$

**Initial Conditions and Input:**

$$\bar{x} = \begin{bmatrix} 0.5961 \\ 0.0529 \\ 0.3177 \\ 0.0002 \end{bmatrix}, \qquad \bar{u} = 0$$

## Scenario: Stability Analysis (Comprehension Exercise)

**Scenario:** Replicate the [[B747 Aircraft Model - 6DOF]] analysis workflow for this biological system.

**Given:** Linearised dynamics matrix $A$ above, initial state $\bar{x}$, zero input.

**Steps:**
1. Compute eigenvalues of $A$ via `eig(A)` in MATLAB.
2. Check signs of real parts — determine [[Internal Stability]] class.
3. Solve Lyapunov equation $A^T P + PA = -Q$ with $Q = I$ via `lyap(A, Q)`.
4. Simulate using `initial(SysC, x0, t)` and plot $V(x) = x^T P x$ over time.

**Final Notes:**
- Inspect $A$ diagonal: most entries are negative → expect a stable response.
- Off-diagonal coupling between $V_m$ and gating variables ($n, m, h$) introduces oscillatory transients — reflecting realistic action potential behaviour.
- Compare Lyapunov function plot shape to the B747 case to understand differences in convergence rates.

## Related Notes
- [[ODE General Solution]]
- [[Analytical Solution - Linear Systems]]
- [[State Transition Matrix]]
- [[Internal Stability]]
- [[Lyapunov Stability]]
- [[Asymptotic Stability]]
- [[B747 Aircraft Model - 6DOF]]
