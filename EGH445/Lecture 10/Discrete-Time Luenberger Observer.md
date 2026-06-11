# Discrete-Time Luenberger Observer

← Back to [[State Estimation: Observers and Output Feedback]]

## Concept

The [[Luenberger Observer]] uses measured output to correct the state estimate, addressing the limitations of open-loop observers that diverge for unstable systems.

## System Model

$$x(kT+T) = Gx(kT) + Hu(kT)$$
$$y(kT) = Cx(kT)$$

(Assuming $D = 0$ for simplicity, can be added back later.)

## Observer Equation

$$\hat{x}(kT+T) = G\hat{x}(kT) + Hu(kT) + L\left(y(kT) - \hat{y}(kT)\right)$$

## Components

| Component | Symbol | Description |
|-----------|--------|-------------|
| State estimate | $\hat{x}(kT)$ | Estimated state at time $kT$ |
| Measured output | $y(kT)$ | Actual measured output |
| Observer gain | $L$ | Gain matrix to be designed |
| Estimated output | $\hat{y}(kT)$ | $\hat{y}(kT) = C\hat{x}(kT)$ |

## Observer Error Dynamics

Define the estimation error $e(kT) = x(kT) - \hat{x}(kT)$. Substituting the observer equation:

$$e(kT+T) = (G - LC)e(kT)$$

The error dynamics are governed by the matrix $(G - LC)$. We design $L$ so that:

- Eigenvalues of $(G - LC)$ are stable (magnitude < 1)
- Error $e(kT)$ converges to zero quickly

## Open-Loop vs Luenberger Observer

| Property | Open-Loop Observer | Luenberger Observer |
|----------|-------------------|---------------------|
| Error dynamics | $e(kT+T) = Ge(kT)$ | $e(kT+T) = (G-LC)e(kT)$ |
| Stability | Depends on $G$ | Determined by $L$ |
| Convergence speed | Fixed by system | Tunable via $L$ |
| Uses output measurement | No | Yes |
