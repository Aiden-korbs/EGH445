# Matched Pole-Zero Method

## 1. Map Poles and Zeros

Map poles and zeros of G_c(s) to poles and zeros of G_d(z) using:

$$z=e^{sT}$$

Form the basic structure:

$$G_d(z)=K_d\frac{\prod(z-z_{z_j})}{\prod(z-z_{p_i})}$$

where z_{z_j} = e^{s_{z_j}T} and z_{p_i} = e^{s_{p_i}T}.

## 2. Adjust Numerator Order (Add Zeros at z = -1)

- Zeros at z = -1 (**Nyquist frequency**) are added to the numerator until its order is equal to or one less than the denominator's order.
- This helps average/smooth the input, similar to Tustin's trapezoidal rule effect.

## 3. Match DC Gain

Adjust K_d so that the DC gain of G_d(z) (at z = 1) matches the DC gain of G_c(s) (at s = 0):

$$G_d(1)=G_c(0)$$

## Properties

- **Stability Preservation**: Poles are mapped such that $|z|=|e^{sT}|=e^{\text{Re}(s)T}<1$, preserving stability of G_c(s).
- **DC Gain Matching**: Ensures low-frequency response of G_d(z) is similar to G_c(s).
- **Comparison to Other Methods**:
  - **Tustin**: Generally better overall frequency response approximation
  - **ZOH**: Exact at sampling instants if input is staircase; can introduce phase lag
  - **MPZ**: Good for preserving specific pole/zero locations and DC gain; often used when locations of dominant poles/zeros are critical

## Implementations

**MATLAB**:
```matlab
Gd = c2d(Gc, T, 'matched')   % or
Gd = c2d(Gc, T, 'mpz')
```

**Python**:
```python
import control
Gd = control.TransferFunction(num, den).sample(T, 'matched')
```
