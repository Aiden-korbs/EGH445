# Disturbances in Discrete-Time State Feedback

## Core Idea
- A standard discrete-time regulation law is
$$
u(kT) = -Kx(kT)
$$
- With an input disturbance $d(kT)$, the dynamics become
$$
x(kT+T) = (G - HK)x(kT) + H_d\,d(kT)
$$
$$
y(kT) = Cx(kT) + Du(kT)
$$

## Interpretation
- Even if the closed-loop poles are stable, a constant input disturbance can shift the output away from the desired equilibrium.
- State feedback alone does **not** guarantee disturbance rejection.

## Why It Matters
- A controller can stabilise the system and still leave a non-zero steady-state error.
- This is the main motivation for [[Integral Action for Disturbance Rejection]].

## Disturbance Model
| Symbol | Meaning |
|---|---|
| $d(kT)$ | disturbance input |
| $H_d$ | disturbance input matrix |
| $K$ | state feedback gain |
| $G-HK$ | closed-loop state matrix |

## Links
- [[Feedforward Disturbance Compensation]]
- [[Integral Action for Disturbance Rejection]]
- [[Tracking vs Regulation]]

## Visual Placeholders
![[State Feedback with Disturbance.png|400]]
