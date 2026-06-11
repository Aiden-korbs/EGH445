# Worked Example: Discretising a Lead Controller

## Given System

**Continuous-Time Lead Controller**:

$$G_c(s)=K\frac{s+a}{s+b}=2.8\frac{s+2}{s+4}$$

**Task**: Find the equivalent discrete-time controller G_d(z) using all three methods for:
- **Part A**: T = 1.0 second
- **Part B**: T = 0.1 second

---

## Part A: T = 1.0s

### Method 1: Tustin (Bilinear) Transform

**Transformation Rule**: $s\leftarrow\frac{2}{T}\frac{z-1}{z+1}=\frac{2(z-1)}{z+1}$ (since T = 1)

$$G_d(z)=2.8\frac{\frac{2(z-1)}{z+1}+2}{\frac{2(z-1)}{z+1}+4}$$

Multiply num/den by (z+1):

$$G_d(z)=2.8\frac{2(z-1)+2(z+1)}{2(z-1)+4(z+1)}=2.8\frac{2z-2+2z+2}{2z-2+4z+4}=2.8\frac{4z}{6z+2}$$

$$G_d(z)=2.8\frac{2z}{3z+1}=\frac{5.6z}{3z+1}=\frac{1.8667z}{z+0.3333}$$

**Result**: $G_d(z)=\frac{1.867z}{z+0.3333}$

**Behaviour**: Stable, poor performance at T = 1.0s.

---

### Method 2: Zero-Order Hold (ZOH) Equivalence

**Transformation Rule**: $G_d(z)=\left(1-z^{-1}\right)\mathcal{Z}\left\{\frac{G_c(s)}{s}\right\}$

**Step 1**: Find G_c(s)/s:

$$\frac{G_c(s)}{s}=2.8\frac{s+2}{s(s+4)}$$

Partial fraction expansion:

$$\frac{s+2}{s(s+4)}=\frac{A}{s}+\frac{B}{s+4}=\frac{0.5}{s}+\frac{0.5}{s+4}$$

$$\frac{G_c(s)}{s}=2.8\left(\frac{0.5}{s}+\frac{0.5}{s+4}\right)=\frac{1.4}{s}+\frac{1.4}{s+4}$$

**Step 2**: Find Z-transform:

$$\mathcal{Z}\left\{\frac{1.4}{s}\right\}=1.4\frac{z}{z-1}$$

$$\mathcal{Z}\left\{\frac{1.4}{s+4}\right\}=1.4\frac{z}{z-e^{-4T}}=1.4\frac{z}{z-e^{-4}}\quad(\text{since }T=1)$$

$$\mathcal{Z}\left\{\frac{G_c(s)}{s}\right\}=1.4\left(\frac{z}{z-1}+\frac{z}{z-e^{-4}}\right)$$

**Step 3**: Calculate G_d(z):

$$G_d(z)=(1-z^{-1})\cdot 1.4\left(\frac{z}{z-1}+\frac{z}{z-e^{-4}}\right)=1.4\left(1+\frac{z-1}{z-e^{-4}}\right)$$

$$G_d(z)=1.4\frac{z-e^{-4}+z-1}{z-e^{-4}}=1.4\frac{2z-(1+e^{-4})}{z-e^{-4}}$$

$$G_d(z)=\frac{2.8z-1.4256}{z-0.0183}$$

**Result**: $G_d(z)=\frac{2.8z-1.4256}{z-0.0183}$

**Behaviour**: Marginally stable, oscillatory behaviour at T = 1.0s.

---

### Method 3: Matched Pole-Zero (MPZ)

**Step 1**: Map Poles and Zeros:

- Zero of G_c(s): $s_z=-2\Rightarrow z_z=e^{-2T}=e^{-2}\approx 0.1353$
- Pole of G_c(s): $s_p=-4\Rightarrow z_p=e^{-4T}=e^{-4}\approx 0.0183$

Basic structure:

$$G_d(z)=K_d'\frac{z-e^{-2}}{z-e^{-4}}$$

**Step 2**: Adjust Numerator Order:

Numerator and denominator are already same order (both first order). No additional zeros at z = -1 needed.

**Step 3**: Match DC Gain:

DC gain of G_c(s): $\lim_{s\to 0}2.8\frac{s+2}{s+4}=2.8\cdot\frac{2}{4}=1.4$

DC gain of G_d(z): $\lim_{z\to 1}K_d'\frac{z-e^{-2}}{z-e^{-4}}=K_d'\frac{1-e^{-2}}{1-e^{-4}}$

Equating:

$$K_d'\frac{1-e^{-2}}{1-e^{-4}}=1.4$$

$$K_d'=1.4\frac{1-e^{-4}}{1-e^{-2}}=1.4\frac{1-0.018316}{1-0.135335}\approx 1.5895$$

$$G_d(z)=1.5895\frac{z-0.1353}{z-0.0183}=\frac{1.5895z-0.2151}{z-0.0183}$$

**Result**: $G_d(z)=\frac{1.5895z-0.2151}{z-0.0183}$

**Behaviour**: Stable, poor performance at T = 1.0s.

---

## Summary of Results (T = 1.0s)

| Method | G_d(z) | Stability |
|---|---|---|
| Tustin | $\frac{1.867z}{z+0.3333}$ | Stable |
| ZOH | $\frac{2.8z-1.4256}{z-0.0183}$ | Marginally stable |
| MPZ | $\frac{1.5895z-0.2151}{z-0.0183}$ | Stable |

---

## Part B: T = 0.1s

At the smaller sampling time T = 0.1s, all three methods will produce better approximations of the original continuous controller, since the discretisation is finer and more closely tracks continuous-time behaviour.

**MATLAB Implementation**:

```matlab
K_c = 2.8;
Gc_s = tf(K_c*[1 2], [1 4]);

% Tustin
T = 1.0;
Gd_tustin = c2d(Gc_s, T, 'tustin')
% Result: (1.867*z)/(z + 0.3333)

% ZOH
Gd_zoh = c2d(Gc_s, T, 'zoh')
% Result: (2.8*z - 1.426)/(z - 0.0183)

% MPZ
Gd_mpz = c2d(Gc_s, T, 'matched')
% Result: (1.59*z - 0.2151)/(z - 0.0183)
```
