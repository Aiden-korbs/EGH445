# Extended Kalman Filter

← Back to [[The Kalman Filter]]

## Problem

The standard [[Kalman Filter]] only handles linear systems. What if the system dynamics or measurement model are nonlinear?

## Nonlinear System Model

$$x(kT+T) = f(x(kT), u(kT)) + w(kT)$$
$$y(kT) = h(x(kT)) + v(kT)$$

## Approach: Linearise at Each Step

Linearise the nonlinear functions $f$ and $h$ around the current state estimate $\hat{x}(kT)$ using **Jacobian matrices**:

**Jacobian of $f$:**

$$G_k = \left. \frac{\partial f}{\partial x} \right|_{\hat{x}(kT), u(kT)}$$

**Jacobian of $h$:**

$$H_k = \left. \frac{\partial h}{\partial x} \right|_{\hat{x}(kT)}$$

Apply the standard KF equations using these time-varying Jacobians $(G_k, H_k)$.

## EKF Algorithm

1. Linearise $f$ and $h$ around $\hat{x}(kT)$ to compute $G_k$ and $H_k$
2. Use $G_k$ as the state transition matrix and $H_k$ as the observation matrix in the standard KF equations
3. The gain $K_k$ and covariance $P_k$ are updated as in the linear KF

## EKF vs Linear KF

| Property | Linear KF | Extended KF |
|----------|-----------|-------------|
| System | Linear | Nonlinear |
| Matrices | Constant $G$, $C$ | Time-varying Jacobians $G_k$, $H_k$ |
| Optimality | Optimal | Not guaranteed (approximation) |
| Computation | Lighter | Heavier (Jacobian at each step) |

## Important Considerations

- **EKF does not guarantee optimality** — linearisation introduces approximations
- **Can diverge** if nonlinearities are severe or initial estimates are poor
- **More computationally intensive** due to Jacobian calculations at each step
- EKF is widely used for nonlinear estimation (e.g., navigation, target tracking)

## Alternatives

Other nonlinear filters exist that avoid direct linearisation:

- **Unscented Kalman Filter (UKF)**: Uses sigma points, avoids Jacobian computation
- **Particle Filter**: Handles severe nonlinearities and non-Gaussian noise, but computationally expensive

EKF is often a good starting point for mildly nonlinear systems.
