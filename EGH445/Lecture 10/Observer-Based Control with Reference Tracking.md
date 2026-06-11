# Observer-Based Control with Reference Tracking

← Back to [[State Estimation: Observers and Output Feedback]]

## Problem

How to achieve $y(kT) \to r(kT)$ for non-zero setpoint tracking when using observer-based control?

## Approach

Using the [[Certainty Equivalence Principle]], replace $x$ with $\hat{x}$ in setpoint regulation schemes and add a feedforward gain $K_r$:

$$u(kT) = -K\hat{x}(kT) + K_r r(kT)$$

Where $K_r$ is chosen to ensure steady-state output matches $r(kT)$.

## Key Considerations

- Finding $K_r$ requires considering the **combined controller-observer dynamics**
- The steady-state analysis must account for both the observer convergence and the controller action
- Any bias in $\hat{x}(kT)$ propagates through $K$ into the control input

## Integral Action Preference

For robust steady-state tracking, [[Integral Action with Observers]] is generally preferred over feedforward-only approaches because:

- Integral action handles model uncertainties and disturbances automatically
- It provides robustness without requiring precise $K_r$ computation
- It accounts for the interaction between observer and controller dynamics
