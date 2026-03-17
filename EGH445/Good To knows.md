## 1. Basic Functions

These are the standard transforms used for simple polynomial or constant terms.

|**Time Domain f(t)**|**Laplace Domain F(s)**|**Notes**|
|---|---|---|
|$\delta(t)$|$1$|Unit Impulse|
|$u(t)$|$\frac{1}{s}$|Unit Step|
|$t$|$\frac{1}{s^2}$|Ramp Function|
|$t^n$|$\frac{n!}{s^{n+1}}$|For $n = 1, 2, 3 \dots$|

---

## 2. Exponential and Trigonometric

These appear most frequently when dealing with the matrix exponential $e^{At}$, especially for systems with oscillation or growth/decay.

|**Time Domain f(t)**|**Laplace Domain F(s)**|
|---|---|
|$e^{at}$|$\frac{1}{s-a}$|
|$\sin(\omega t)$|$\frac{\omega}{s^2 + \omega^2}$|
|$\cos(\omega t)$|$\frac{s}{s^2 + \omega^2}$|
|$\sinh(at)$|$\frac{a}{s^2 - a^2}$|
|$\cosh(at)$|$\frac{s}{s^2 - a^2}$|

---

## 3. Shifting and Damping

If your matrix $A$ has complex eigenvalues, you will likely see these "S-domain shifting" forms during your partial fraction expansion.

|**Time Domain f(t)**|**Laplace Domain F(s)**|
|---|---|
|$e^{at}t^n$|$\frac{n!}{(s-a)^{n+1}}$|
|$e^{at}\sin(\omega t)$|$\frac{\omega}{(s-a)^2 + \omega^2}$|
|$e^{at}\cos(\omega t)$|$\frac{s-a}{(s-a)^2 + \omega^2}$|

---

## 4. Key Operational Properties

When manipulating the $(sI - A)^{-1}$ matrix algebraically, these properties help you move between domains.

- **Linearity:** $\mathcal{L}\{af(t) + bg(t)\} = aF(s) + bG(s)$
    
- **Time Scaling:** $\mathcal{L}\{f(at)\} = \frac{1}{a}F(\frac{s}{a})$
    
- **Frequency Shift:** $\mathcal{L}\{e^{at}f(t)\} = F(s-a)$
    
- **Differentiation:** $\mathcal{L}\{f'(t)\} = sF(s) - f(0)$

