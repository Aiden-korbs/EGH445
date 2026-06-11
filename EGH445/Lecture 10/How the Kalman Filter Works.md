# How the Kalman Filter Works

← Back to [[The Kalman Filter]]

The Kalman Filter operates in two alternating steps: **Prediction** and **Correction**.

## Prediction (Time Update)

Projects state estimate and error covariance forward using the system model $(G, H)$ and process noise covariance $Q$.

**Predicted State:**

$$\hat{x}^-(kT) = G\hat{x}(kT-T) + Hu(kT-T)$$

**Predicted Covariance:**

$$P^-(kT) = GP(kT-T)G^\top + Q$$

| Goal | Predict $\hat{x}^-(kT)$ and $P^-(kT)$ at time $kT$ based on previous estimate |
|------|---------------------------------------------------------------------------------|

## Correction (Measurement Update)

Updates the predicted estimate using actual measurement $y(kT)$, weighted by the Kalman Gain $K_k$.

**Kalman Gain:**

$$K_k = P^-(kT)C^\top \left(CP^-(kT)C^\top + R\right)^{-1}$$

**Updated State:**

$$\hat{x}(kT) = \hat{x}^-(kT) + K_k \left(y(kT) - C\hat{x}^-(kT)\right)$$

**Updated Covariance:**

$$P(kT) = \left(I - K_kC\right)P^-(kT)$$

| Goal | Correct predicted state and error covariance using measurement $y(kT)$ |
|------|------------------------------------------------------------------------|

## Cycle

1. **Predict** using system model and process noise statistics
2. **Correct** using measurement and measurement noise statistics
3. Updated $\hat{x}(kT)$ and $P(kT)$ become inputs for the next prediction step

## Comparison with Luenberger Observer

Both use a predictor-corrector structure, but:

- **Kalman Filter**: gain $K_k$ is computed optimally from noise statistics $(Q, R)$
- **Luenberger Observer**: gain $L$ is fixed from pole placement
