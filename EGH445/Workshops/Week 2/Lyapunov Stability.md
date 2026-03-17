← Back to [[Week 2 Workshop - System Response and Stability]]

# Lyapunov Stability

## Core Idea
Stability is analysed through an **energy-like function** $V(x)$ — if the system's "energy" is decreasing, the system is stable.

## Setup
Consider the LTI system $\dot{x} = Ax$ and a **positive definite** energy function $V(x)$:

$$V(x) > 0 \quad (x \neq 0), \qquad V(0) = 0$$

![[Lyapunov Energy Bowl Diagram.png|400]]

## Stability via Derivative $\dot{V}(x)$

| Condition | Interpretation |
| :--- | :--- |
| $\dot{V}(x) \leq 0$ | Energy **decreasing** → system **stable** |
| $\dot{V}(x) > 0$ | Energy **increasing** → system **unstable** |

## Lyapunov Definition
**Lyapunov stability** means the system trajectory **stays in a local region** near the equilibrium point:

$$x(t) \in \mathcal{R} \quad \text{as} \quad t \to \infty$$

> Compare with [[Asymptotic Stability]], which requires $x(t) \to 0$.

## Lyapunov Function for LTI Systems
Choose:

$$V(x) = x^T P x, \quad P > 0 \text{ (Symmetric Positive Definite)}$$

Then:

$$\dot{V}(x) = -x^T Q x$$

Linking to the **Lyapunov Equation**:

$$A^T P + P A = -Q$$

- If $Q \geq 0$ (positive semi-definite) → $\dot{V}(x) \leq 0$ → **Lyapunov stable**, $\text{Re}(\lambda_i) \leq 0$
- If $Q > 0$ (positive definite) → $\dot{V}(x) < 0$ → **Asymptotically stable**, $\text{Re}(\lambda_i) < 0$

## Related Notes
- [[Asymptotic Stability]]
- [[Internal Stability]]
- [[State Transition Matrix]]
- [[B747 Aircraft Model - 6DOF]]
