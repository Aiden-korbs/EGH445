# Tracking and Internal Model Principle

## Tracking Problem
- Regulation handles **constant references**.
- Tracking is harder because the reference changes with time, for example:
$$
r(kT) = \sin(kT)
$$

## Limitation of Standard Feedforward Gain
- The steady-state gain method
$$
K_r = \left[C\left(I - (G - HK)\right)^{-1}H\right]^{-1}
$$
assumes the reference is **constant**.

## Internal Model Principle
- For asymptotic tracking or disturbance rejection, the controller must include the dynamics that generate the reference or disturbance.

## Common Reference Models
| Signal Type | Signal | $R(z)$ |
|---|---|---|
| Constant / step | $r(kT)=1$ | $R(z)=\dfrac{z}{z-1}$ |
| Ramp | $r(kT)=t$ | $R(z)=\dfrac{Tz}{(z-1)^2}$ |
| Sinusoid | $r(kT)=\sin(\omega t)$ | $R(z)=\dfrac{\sin \omega}{z^2 - 2\cos(\omega)z + 1}$ |

## Interpretation
- **Integral action** already embeds the step model:
$$
\frac{1}{z-1}
$$
- For a ramp, a double-integrator style augmentation is needed.
- For a sinusoid, the controller must include oscillator dynamics.

## Example Oscillator Augmentation
- Define:
$$
z(kT) \triangleq \begin{bmatrix} x(kT) \\ q_1(kT) \\ q_2(kT) \end{bmatrix}
$$

- Error-driven oscillator states can be written as:
$$
q_1(kT+T) = q_2(kT)
$$

$$
q_2(kT+T) = -q_1(kT) + 2\cos(\omega)q_2(kT) + e(kT)
$$

## Practical Implications
- Works well when the reference or disturbance model is known.
- Performance depends strongly on knowing the correct frequency $\omega$.
- Complexity and controller order increase.
- Transients can become harder, especially when the signal starts or stops abruptly.

## Links
- [[Integral Action in Discrete-Time Control]]
- [[Disturbances in Discrete-Time Control]]

## Visual Placeholders
![[Tracking Sinusoidal Reference.png|400]]
![[Internal Model Principle Summary.png|400]]
