← Back to [[Discrete-time Control System Modelling]]

# Zero Order Hold and Data Hold

## Definition
**Data hold** is the process of generating a continuous-time signal $u(t)$ from a discrete-time sequence $u(kT)$ by holding the sampled value over the sampling period $T$:

$$kT < t < kT + T$$

## nth Order Polynomial Approximation
The held signal can be approximated using an $n$th order polynomial in time $\tau$ where $0 < \tau < T$, with the output fixed at $u(kT)$ at $\tau = 0$:

$$u(kT + \tau) = a_n\tau^n + a_{n-1}\tau^{n-1} + \cdots + a_1\tau + a_0$$

- The **order** determines how many past input values are used to extrapolate the held signal over $T$.
- Higher order → more accurate reconstruction, but more **delay/lag** introduced.

> **Trade-off:** Higher order holds are more accurate but introduce undesirable delay. In EGH445, only **ZOH** is in scope — FOH and above are out of scope.

## Zero Order Hold (ZOH)

$$\boxed{u(kT + \tau) = u(kT)}$$

- Simply holds the last sample value constant for the entire interval $[kT, kT+T)$.
- No past values needed — zero delay beyond the sampling period itself.

![[ZOH Signal Diagram.png|400]]

### Laplace Transform of ZOH

$$\boxed{U(s) = \frac{1 - e^{-Ts}}{s}}$$

> This transfer function is important for control system analysis and design with discrete-time controllers.

## First Order Hold (FOH) — For Reference

$$u(kT + \tau) = u(kT) + \frac{u(kT) - u(kT - T)}{T} \cdot \tau, \quad \tau \in (0, T)$$

- Uses the current and previous sample to linearly extrapolate.
- More accurate than ZOH but introduces additional lag — **out of scope for EGH445**.

## Hold Methods Summary

| Method | Formula | Past Values Used | Accuracy | Delay |
| :--- | :--- | :--- | :--- | :--- |
| **ZOH** | $u(kT)$ | 0 | Lower | Minimal |
| **FOH** | Linear extrapolation | 1 | Higher | More |
| **nth Order** | Polynomial | $n$ | Highest | Most |

## Related Notes
- [[Continuous vs Digital Control Architecture]]
- [[Discrete Signal Representation]]
- [[Discrete State Space Models - Overview]]
