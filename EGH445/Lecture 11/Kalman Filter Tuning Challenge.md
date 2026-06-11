# Kalman Filter Tuning Challenge

## KF Fundamentals Recap

**Optimal state estimator for linear systems with Gaussian noise.**

### System Model with Noise

$$x(kT+T)=Gx(kT)+Hu(kT)+w(kT)$$
$$y(kT)=Cx(kT)+v(kT)$$

- w(kT): Process noise, Q = E[ww^\top]
- v(kT): Measurement noise, R = E[vv^\top]

### Recursive Structure (Predict-Correct)

**1. Predict**: Project state estimate $\hat{x}$ forward using the model (G, H, Q):

$$\hat{x}^-(kT)=G\hat{x}(kT-T)+Hu(kT-T)$$
$$P^-(kT)=GP(kT-T)G^\top+Q_{k-1}$$

**2. Correct (Update)**: Adjust prediction using the current measurement y(kT) and the calculated Kalman Gain K_k:

$$K_k=P^-(kT)C^\top\left(CP^-(kT)C^\top+R\right)^{-1}$$
$$\hat{x}(kT)=\hat{x}^-(kT)+K_k\left(y(kT)-C\hat{x}^-(kT)\right)$$
$$P(kT)=\left(I-K_kC\right)P^-(kT)$$

### Key Idea

K_k optimally balances trusting the model prediction vs. trusting the noisy measurement based on the relative sizes of P^-(kT), Q, and R.

## The Tuning Challenge

**"Optimal" performance relies on having the correct noise covariance matrices Q and R.**

- **R** — sensor measurement uncertainty (variance)
- **Q** — dynamics model uncertainty (variance) introduced by unmodelled forces, discretisation errors, etc.

**The Problem**: In most real-world applications, the true values of Q and R are **unknown**.

**Consequence**: Choosing incorrect Q and R leads to suboptimal state estimates.

| If Q/R ratio is... | Filter behaviour | Result |
|---|---|---|
| **Too small** | Trusts the model too much, ignores useful measurements | Estimates converge slowly and may drift |
| **Too large** | Trusts measurements too much, ignores the model | Estimates become noisy |

> Q and R often become **tuning parameters** adjusted based on observed filter performance, rather than precisely known quantities.
