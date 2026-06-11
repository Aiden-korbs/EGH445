# The Kalman Filter

← Back to [[State Estimation: Observers and Output Feedback]]

## Motivation

The [[Discrete-Time Luenberger Observer]] assumes a deterministic model with no noise. Limitations:

- Observer gain $L$ is chosen from pole locations, not noise characteristics
- Process noise (uncertainties in dynamics) and measurement noise (sensor errors) degrade performance
- Large gains for fast convergence amplify measurement noise

The **Kalman Filter** is an optimal estimator for linear systems subject to Gaussian noise.

## Stochastic System Model

**Process noise** $w(kT)$: Uncertainty in system dynamics, characterised by covariance $Q$.

**Measurement noise** $v(kT)$: Uncertainty in sensor measurements, characterised by covariance $R$.

$$x(kT+T) = Gx(kT) + Hu(kT) + w(kT)$$
$$y(kT) = Cx(kT) + v(kT)$$

## Key Properties

| Property | Description |
|----------|-------------|
| Recursive | Uses previous estimate and current measurement |
| Predictor-Corrector | Predicts forward, then corrects with measurement |
| Optimal Gain | $K_k$ minimises estimated error covariance $P_k$ |
| Noise-Aware | Balances model prediction vs. noisy measurement via $Q$ and $R$ |

## Kalman Filter vs Luenberger Observer

| Aspect | Luenberger Observer | Kalman Filter |
|--------|---------------------|---------------|
| Noise model | None | Explicit ($Q$, $R$) |
| Gain design | Pole placement | Optimal (minimises $P_k$) |
| Gain | Constant $L$ | Time-varying $K_k$ |
| Optimality | Subjective (pole choice) | Optimal for Gaussian noise |

## Design Trade-off

The Kalman gain $K_k$ optimally balances:

- **Trusting the model**: favoured when $Q$ is small relative to $R$
- **Trusting the measurement**: favoured when $R$ is small relative to $Q$

This makes the Kalman Filter superior to the Luenberger Observer in noisy environments.
