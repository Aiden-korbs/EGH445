# Tustin Bilinear Transform

## Derivation from Trapezoidal Integration

Approximates the continuous-time integration operator 1/s with a discrete-time equivalent derived from the trapezoidal rule:

$$u(kT)=\int e(t)dt\quad\rightarrow\quad u(kT)\approx u(kT-T)+\frac{T}{2}\left(e(kT)+e(kT-T)\right)$$

Taking the z-transform of both sides:

$$U(z)=z^{-1}U(z)+\frac{T}{2}\left(E(z)+z^{-1}E(z)\right)$$

$$\frac{U(z)}{E(z)}=\frac{T}{2}\frac{1+z^{-1}}{1-z^{-1}}$$

## Transformation Rule

To convert G_c(s) to G_d(z), substitute s in G_c(s) with:

$$s\leftarrow\frac{2}{T}\frac{z-1}{z+1},\quad\text{that is,}\quad G_d(z)=G_c\left(\frac{2}{T}\frac{z-1}{z+1}\right)$$

## Properties

- Maps the **left-half** of the s-plane entirely into the **unit circle** in the z-plane.
- Maps the **j\omega axis** of the s-plane onto the unit circle $|z|=1$ in the z-plane.
- **Preserves stability**: a stable G_c(s) will result in a stable G_d(z).

## Implementations

**MATLAB**:
```matlab
Gd = c2d(Gc, T, 'tustin')
```

**Python**:
```python
from scipy import signal
Gd = signal.cont2discrete(Gc, dt=T, method='bilinear')
```
