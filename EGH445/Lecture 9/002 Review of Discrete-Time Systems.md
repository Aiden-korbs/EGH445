# Review of Discrete-Time Systems

## Continuous-Time Systems

A general continuous-time system is described by:

$$\dot{x}(t) = f(x, u)$$
$$y(t) = g(x, u)$$

## Linearised System

Linearising around an equilibrium point $(\bar{x}, \bar{u})$ where $\delta x = x - \bar{x}$, $\delta u = u - \bar{u}$, $\delta y = y - \bar{y}$:

$$\delta \dot{x}(t) = A \delta x(t) + B \delta u(t)$$
$$\delta y(t) = C \delta x(t) + D \delta u(t)$$

The Jacobian matrices are:

$$A = \frac{\partial f}{\partial x}\bigg|_{\bar{x},\bar{u}}, \quad B = \frac{\partial f}{\partial u}\bigg|_{\bar{x},\bar{u}}, \quad C = \frac{\partial g}{\partial x}\bigg|_{\bar{x},\bar{u}}, \quad D = \frac{\partial g}{\partial u}\bigg|_{\bar{x},\bar{u}}$$

## Discretisation

The continuous-time system is discretised with sampling time $T$:

$$x(kT + T) = G x(kT) + H u(kT)$$
$$y(kT) = C x(kT) + D u(kT)$$

where:

$$G = e^{AT}$$
$$H = \left[\int_{0}^{T} e^{A\tau} d\tau\right] B$$

If $A$ is invertible:

$$H = A^{-1}(G - I)B$$

## State-Feedback Controller

The state-feedback controller is:

$$u(kT) = -K x(kT)$$

where $K$ is the feedback gain matrix designed to move the poles of the closed-loop system.

The closed-loop dynamics become:

$$x(kT + T) = (G - HK) x(kT)$$

## Pole Placement

Pole placement achieves desired closed-loop poles by equating the characteristic polynomial:

$$\det(zI - (G - HK)) = (z - z_1)(z - z_2) \cdots (z - z_n)$$

**Important:** The solution exists if the system is controllable, i.e., the controllability matrix $\mathcal{C} = [H, GH, G^2H, \dots, G^{n-1}H]$ has full rank ($\text{rank}(\mathcal{C}) = n$).

## Pole Selection

Desired pole locations are related to time-domain specifications:

| Specification | Symbol | Formula |
|---|---|---|
| Settling time | $t_s$ | — |
| Rise time | $t_r$ | — |
| Percent overshoot | %OS | — |
| Natural frequency | $\omega_n$ | $\omega_n = \frac{\zeta t_s}{\ln(\%OS/100)}$ |
| Damping ratio | $\zeta$ | $\zeta = \frac{\ln(\%OS/100)}{\sqrt{\pi^2 + \ln^2(\%OS/100)}}$ |
| Continuous poles | $s_{1,2}$ | $s_{1,2} = -\zeta\omega_n \pm j\omega_n\sqrt{1-\zeta^2}$ |
| Discrete poles | $z_{1,2}$ | $z_{1,2} = e^{s_{1,2}T}$ |

## Internal Model Principle

Integral action is used to reject disturbances or track references with known models (step, ramp, sinusoidal inputs). This approach still relies on pole placement.

## Key Takeaways

- Continuous-time systems are linearised around equilibrium points via Jacobian matrices
- Discretisation converts $A, B$ to $G, H$ using matrix exponential formulas
- State-feedback $u(kT) = -Kx(kT)$ yields closed-loop dynamics $x(kT+T) = (G - HK)x(kT)$
- Pole placement requires controllability and a mapping from time-domain specs to pole locations
- Pole placement does not account for control effort or handle MIMO/stiff/nonlinear systems well
