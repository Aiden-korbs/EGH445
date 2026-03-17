← Back to [[Discrete-time Control System Modelling]]

# Discrete Signal Representation

## Sampled Signals — Continuous to Discrete Time

A sampler converts $x(t)$ into a train of impulses $x^*(t)$ where each impulse has a magnitude equal to $x(t)$ at the corresponding sample time $kT$.

$$x^*(t) = \sum_{k=0}^{\infty} x(kT)\,\delta(t - kT)$$

$$x^*(t) = x(0)\delta(t) + x(T)\delta(t-T) + \cdots + x(kT)\delta(t-kT)$$

![[Impulse Sampler Diagram.png|400]]

## Frequency Domain (Laplace) Representation

Taking the Laplace transform of the sampled signal:

$$X^*(s) = \mathcal{L}\{x^*(t)\} = x(0)\mathcal{L}\{\delta(t)\} + \cdots + x(kT)\mathcal{L}\{\delta(t-kT)\}$$

$$X^*(s) = x(0) + x(T)e^{-Ts} + \cdots + x(kT)e^{-kTs}$$

$$\boxed{X^*(s) = \sum_{k=0}^{\infty} x(kT)\,e^{-kTs}}$$

> This form is useful when analysing control systems in the frequency domain and leads directly to the **Z-transform**.

## Alternate Interpretation

The sampled signal can also be viewed as the **product** of the input signal $x(t)$ and a train of unit impulses:

$$\delta_T = \sum_{k=0}^{\infty} \delta(t - kT)$$

So the sampler acts as a **modulator**, with $\delta_T$ as the carrier and $x(t)$ as the modulating signal.

> **Note:** The impulse sampler is a mathematical fiction — real sampling takes finite time. However, if the sampling time is small relative to the system time constant, and the sampler is connected to a ZOH, the approximation is valid for analysis and design.

## Related Notes
- [[Continuous vs Digital Control Architecture]]
- [[Sampling Time and Frequency Selection]]
- [[Zero Order Hold and Data Hold]]
