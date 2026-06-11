# Observer Trade-offs

## Observer Performance

- **Luenberger poles** determine error convergence speed. Faster poles $\rightarrow$ potentially higher gain L.
- **Kalman Filter** dynamic gain K_k minimises the estimation error covariance iteratively, balancing model trust vs measurement trust based on noise characteristics (Q, R).

## Noise Amplification

- Large observer gains (L or K_k) can amplify measurement noise v(kT), negatively impacting the control input $u(kT)=-K\hat{x}(kT)$.
- **Trade-off**: fast estimation vs noise sensitivity.

## Computational Load

Observers add computational cost (matrix multiplications, additions).

- Increase in computational cost: **Luenberger Observer < Kalman Filter < Extended Kalman Filter (EKF)**
- Needs to be feasible on target hardware, considering the selected/needed sampling time T.

## Certainty Equivalence Principle

- Controller (K) and Observer (L) can be designed **independently**.
- This holds perfectly if the model is perfect.
- Model mismatch can affect performance.
- Sometimes **detuning the observer** (slower poles) can improve robustness in practice.

## Benefits vs Costs of State Estimation

| Benefits of State Estimation | Costs of State Estimation |
|---|---|
| Handling unmeasured states | Added complexity (and computational load) |
| Better performance via full state feedback | Need of tuning |
| | Sensitivity to noise |
| | Model mismatch |

> Depends on the application!
