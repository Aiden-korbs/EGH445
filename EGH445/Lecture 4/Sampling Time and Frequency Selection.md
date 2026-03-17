← Back to [[Discrete-time Control System Modelling]]

# Sampling Time and Frequency Selection

## Core Question
> How fast (or slow) should we sample? How do we select $T$ in our samplers?

## Sampling Parameters

$$T = \frac{1}{f_s}, \qquad f_s = \frac{1}{T}$$

- $T$ — **sampling period** (time between samples)
- $f_s$ — **sampling frequency** (samples per second)
- $\omega_s = 2\pi f_s$ — sampling frequency in rad/s

## Factors in Choosing Sampling Time

| Factor | Description |
| :--- | :--- |
| **Tracking Effectiveness** | Ability to track a reference input at a certain frequency |
| **Regulation Effectiveness** | Ability to reject or manage disturbances (plant and measurement noise) |
| **Cost** | Hardware and sensors are cheaper at lower sampling rates; higher rates are more expensive |

## Cost vs Performance Trade-off

- **Low sampling rate:** cheaper hardware and sensors; more time for the computer to solve control problems — but poorer system performance.
- **High sampling rate:** better performance, more accurate signal reconstruction — but higher cost and computational demand.

## Aliasing

- **Aliasing** plays a major role in digital control system performance (both tracking and regulation effectiveness).
- The concept of **aliasing and folding** must be understood to choose an appropriate sampling rate.
- This is covered in detail in the next lecture.

## Impact on Discrete State Space Model
The choice of $T$ directly affects the matrices $G$ and $H$ in the [[Discrete State Space Models - Overview|discrete state space model]]:

$$G = e^{AT}, \qquad H = \int_0^T e^{A\lambda} d\lambda\, B$$

- A **stable continuous-time system** may become **unstable** when sampled at a poor choice of $T$.
- As $T \ll 1$: $G \approx I$, meaning the next state is approximately the current state plus input $Hu(kT)$.

## Related Notes
- [[Continuous vs Digital Control Architecture]]
- [[Discrete Signal Representation]]
- [[Discrete State Space Models - Overview]]
