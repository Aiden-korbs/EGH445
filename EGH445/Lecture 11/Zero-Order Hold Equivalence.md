# Zero-Order Hold Equivalence

## ZOH Assumption

Assumes the input e(t) to the controller is held constant by a **Zero-Order Hold (ZOH)** for one sampling period T:

$$e(kT+\tau)=e(kT)\quad\text{for }0\leq\tau<T$$

- The sampler and ZOH are placed before the continuous controller G_c(s).
- The continuous controller sees a **staircase input**: e(t) = e(kT) for kT \leq t < kT + T.
- The result is z-transformed to get the discrete controller G_d(z).

## ZOH Transfer Function

$$G_{zoh}(s)=\frac{1}{s}\left(1-e^{-sT}\right)$$

Positive step at kT minus negative step at kT + T.

## Transformation Rule

The pulse transfer function G_d(z) of the discretised controller is given by:

$$G_d(z)=\mathcal{Z}\left\{\mathcal{L}^{-1}\left[\frac{1-e^{-sT}}{s}G_c(s)\right]\right\}=\left(1-z^{-1}\right)\mathcal{Z}\left\{\frac{G_c(s)}{s}\right\}$$

## Properties

- **Exact at sampling instants** if the input to G_c(s) were indeed staircase (due to the ZOH).
- **Stability is preserved** if G_c(s) is stable.

## Implementations

**MATLAB**:
```matlab
Gd = c2d(Gc, T, 'zoh')
```

**Python**:
```python
from scipy import signal
Gd = signal.cont2discrete(Gc, dt=T, method='zoh')
```
