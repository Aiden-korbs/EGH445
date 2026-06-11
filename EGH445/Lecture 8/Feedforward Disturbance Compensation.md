# Feedforward Disturbance Compensation

## Key Idea
- If the disturbance is known, a feedforward term can be added:
$$
u(kT) = -Kx(kT) + u_{ff}
$$

## Closed-Loop Dynamics
$$
x(kT+T) = (G-HK)x(kT) + H_d\,d(kT) + H\,u_{ff}
$$

## Ideal Cancellation
- To cancel the disturbance exactly, choose
$$
u_{ff} = -H^{-1}H_d\,d(kT)
$$

## Limitation
- This requires:
  - exact knowledge of $d(kT)$
  - an accurate model for $H$ and $H_d$
- In practice, model mismatch breaks perfect cancellation.

## Practical Consequence
- Feedforward works well for **known** disturbances.
- It is not robust against:
  - parameter uncertainty
  - unknown disturbances
  - modelling errors

## Comparison
| Method | Strength | Weakness |
|---|---|---|
| Feedforward | Can cancel known disturbance directly | Sensitive to model error |
| Integral action | Robust to constant disturbance/error | Adds states and can affect transient response |

## Links
- [[Disturbances in Discrete-Time State Feedback]]
- [[Integral Action for Disturbance Rejection]]
- [[Mass-Spring-Damper Design 2 Example]]

## Visual Placeholders
![[Feedforward Disturbance Rejection.png|400]]
