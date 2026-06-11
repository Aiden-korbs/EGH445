# Sinusoidal Tracking by Augmentation

## Goal
- Track a sinusoidal reference such as
$$
r(kT) = \sin(kT)
$$
with small steady-state error.

## Error-Driven Oscillator
Define
$$
q(kT) = \begin{bmatrix}q_1(kT)\\ q_2(kT)\end{bmatrix}
$$
with
$$
q_1(kT+T) = q_2(kT)
$$
$$
q_2(kT+T) = -q_1(kT) + 2\cos(\omega)\,q_2(kT) + e(kT)
$$

## Augmented System
Let the full state be
$$
z(kT) = \begin{bmatrix}x(kT)\\ q_1(kT)\\ q_2(kT)\end{bmatrix}
$$

Then the controller is designed as
$$
u(kT) = -K_z z(kT)
$$

## Key Insight
- The added controller states behave like an internal oscillator.
- This is why sinusoidal tracking needs more than simple integral action.

## Scenario
### Scenario
Design a discrete-time controller that tracks a known sinusoid.

### Given
- Plant matrices $G$, $H$, $C$
- Frequency $\omega$
- Error:
$$
e(kT) = r(kT) - y(kT)
$$

### Steps
1. Define the oscillator states $q_1$, $q_2$.
2. Build the augmented state $z$.
3. Form the augmented matrices for the plant plus internal model.
4. Choose desired augmented closed-loop poles.
5. Compute $K_z$ by pole placement.
6. Simulate the response to verify phase lag and amplitude error.

### Final Notes
- The controller must contain the sinusoidal generator dynamics.
- This is a direct application of the [[Internal Model Principle]].

## Links
- [[Internal Model Principle]]
- [[Dynamic Extension for Step Ramp and Sinusoidal References]]
- [[Mass-Spring-Damper Design 2 Example]]

## Visual Placeholders
![[Sinusoidal Internal Model.png|400]]
