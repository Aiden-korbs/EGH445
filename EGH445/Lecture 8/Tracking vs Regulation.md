# Tracking vs Regulation

## Regulation
- **Regulation** means driving the output to a fixed target.
- Common cases:
  - zero reference:
$$
r(kT) = 0
$$
  - constant reference:
$$
r(kT) = \bar{y}
$$

## Tracking
- **Tracking** means forcing the output to follow a time-varying reference:
$$
r(kT) = r_k
$$
- Example used in the lecture:
$$
r(kT) = \sin(kT)
$$

## Main Difference
| Problem | Target |
|---|---|
| Regulation | fixed equilibrium or constant setpoint |
| Tracking | changing signal over time |

## Why Integral Action Is Not Enough
- A single integrator is ideal for constant references and constant disturbances.
- It does not automatically embed the dynamics needed for exact sinusoidal tracking.

## Key Question
- What controller structure contains the dynamics of the signal we want to follow?
- This leads to the [[Internal Model Principle]].

## Links
- [[Non-Zero Regulation with Integral Action]]
- [[Internal Model Principle]]
- [[Dynamic Extension for Step Ramp and Sinusoidal References]]

## Visual Placeholders
![[Regulation vs Tracking.png|400]]
