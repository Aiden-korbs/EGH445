# 6DOF Aircraft Workshop Example

## Purpose
- The workshop uses a **6DOF aircraft model** as an applied example for direct discrete-time control design.

## What the Example Covers
- Real system
- Real system model and approximations
- Expected system characteristics
- Direct controller design

## Why It Is Used
- Regulate aircraft behaviour
- Improve performance
- Simulate and test safely
- Support implementation thinking

## Longitudinal Model Assumptions
- Motion is considered near:
  - **straight and level flight**
  - **constant velocity**
- The model is **linearised** about an equilibrium point.

## Longitudinal States
- The model describes:
  - forward velocity change $u$
  - upward velocity change $w$
  - pitch angle $\theta$
  - pitch rate $q = \dot{\theta}$

## Discrete Model Assumptions
- Sampling time:
$$
T = 0.01
$$
- Thrust input is assumed zero.
- Control is applied through the **elevator** $\delta_e$.

## Sensor Choice
- In the Week 8 workshop, the model uses:
$$
C = [0\;0\;0\;1]
$$
- This means only **pitch angle** is measured.

## Controllability and Observability Result
| Property | Rank Result | Conclusion |
|---|---|---|
| Controllability of augmented model | $5$ | Controllable |
| Observability of plant model | $4$ | Observable |

## Links
- [[Augmented Aircraft Model for Integral Action]]
- [[Aircraft Response Evaluation]]
- [[Aircraft State Variable Reference]]

## Visual Placeholders
![[Aircraft Longitudinal Model.png|400]]
![[Aircraft Discrete Model.png|400]]
