# Internal Model Principle

## Statement
- For a stable closed-loop system to achieve asymptotic tracking of a reference $r(t)$, or rejection of a disturbance $d(t)$, the controller must include the dynamics that generate that signal inside the feedback loop.

## Meaning
- The controller must contain a model of the signal class:
  - step
  - ramp
  - sinusoid
  - other structured exogenous signals

## Common Reference Models
| Signal | Time-Domain Form | $\mathcal{Z}$-Domain Form |
|---|---|---|
| Constant/step | $r(kT)=1$ | $R(z)=\dfrac{z}{z-1}$ |
| Ramp | $r(kT)=t$ | $R(z)=\dfrac{Tz}{(z-1)^2}$ |
| Sinusoid | $r(kT)=\sin(\omega t)$ | $R(z)=\dfrac{\sin\omega}{z^2-2\cos\omega\,z+1}$ |

## Interpretation
- A single integrator
$$
\frac{1}{z-1}
$$
captures step-like dynamics.
- A double-integrator-type augmentation is needed for ramp tracking.
- Oscillatory internal dynamics are needed for sinusoidal tracking.

## Why This Matters
- Better tracking is not just about tuning gains.
- It is about matching controller structure to signal structure.

## Links
- [[Dynamic Extension for Step Ramp and Sinusoidal References]]
- [[Sinusoidal Tracking by Augmentation]]
- [[Integral Action for Disturbance Rejection]]

## Visual Placeholders
![[Internal Model Principle Overview.png|400]]
