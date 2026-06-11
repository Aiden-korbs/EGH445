# Residual Analysis for KF Tuning

## Residual Definition

The residual is the difference between the actual measurement and the predicted measurement at each step:

$$e(kT)=y(kT)-\hat{y}^-(kT)=y(kT)-C\hat{x}^-(kT)$$

## Theoretical Properties

For a perfectly modelled and optimally tuned Kalman filter:

- **Zero-mean**: $E[e(kT)] = 0$
- **White noise**: Uncorrelated over time, $E[e(kT)e(jT)^\top] = 0 for k \neq j$
- **Known Covariance**: $E[e(kT)e(kT)^\top] = CP^-(kT)C^\top + R_k$

## Practical Tuning Workflow

1. **Collect Residuals**: Record e(kT) over a representative run.
2. **Check Mean**: If significantly non-zero $\rightarrow$ bias in sensors or in the system model.
3. **Check Whiteness**: Plot the **autocorrelation function (ACF)** of the residuals.

## Iterative Q/R Adjustment

Adjust Q and R iteratively until the residuals "look like" zero-mean white noise with the expected covariance.

| Residual Symptom | Possible Issue | Adjustment |
|---|---|---|
| Non-zero mean | Sensor bias or model bias | Check sensor calibration / model accuracy |
| Correlated (ACF not decaying) | Q/R mismatch | Increase R or decrease Q if correlated; adjust iteratively |
| Variance too high | R too small or Q too large | Increase R or decrease Q |
| Variance too low | R too large or Q too small | Decrease R or increase Q |
