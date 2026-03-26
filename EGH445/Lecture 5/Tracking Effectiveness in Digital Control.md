# Tracking Effectiveness in Digital Control

## Key Idea
- The controller must sample the **reference command** correctly.
- If the reference is aliased, the controller may try to track the **wrong command**.

## Important Distinction
- Do not confuse:
  - **reference/system frequency** $f$
  - **sampling frequency** $f_s$

## Lower Bound from Tracking
- If the command contains frequencies up to $f$, then:
$$
f_s > 2f
$$
- This is the minimum condition for **unambiguous reconstruction**.

## Practical Performance Choice
- Meeting Nyquist only guarantees the correct frequency content is not aliased.
- It does **not** guarantee accurate signal shape capture.
- For good tracking quality:
$$
f_s \ge 10f
$$
is a common minimum practical target.

## Multi-Sine Reference Example
- A reference may be made from multiple sinusoidal components:
$$
x(t) = x_1(t) + x_2(t)
$$
- Example structure:
$$
x_1(t) = \cos(2\pi f_1 t), \qquad x_2(t) = \sin(2\pi f_2 t)
$$
- The highest frequency component determines the Nyquist requirement.

## Interpretation of the Three Cases
| Sampling Choice | Outcome |
|---|---|
| $f_s \ll 2f$ | Reference is aliased, wrong command is tracked |
| $f_s = 2f$ | Correct main frequency but poor shape capture |
| $f_s \gg 2f$ | Correct frequency and much better shape capture |

## Practical Consequence
- If the reference is under-sampled:
  - the error signal $e(k)$ is wrong
  - the controller acts on false information
- If the reference is well sampled:
  - the sampled signal reflects the real command
  - tracking can be close to continuous-time behavior

## Links
- [[Sampling Time Selection]]
- [[Aliasing and Nyquist Criterion]]
- [[Discrete-Time System Response]]

## Visuals
![[Tracking Aliased Reference.png|400]]
![[Tracking Nyquist-Limit Reference.png|400]]
![[Tracking Well-Sampled Reference.png|400]]
