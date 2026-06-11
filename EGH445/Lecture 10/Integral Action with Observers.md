# Integral Action with Observers

← Back to [[State Estimation: Observers and Output Feedback]]

## Concept

Observers can estimate disturbances, which can then be used to effectively implement integral action for robust tracking and rejection.

## Disturbance-Augmented Observer

The observer is augmented with a state that estimates the disturbance:

$$\hat{z}(kT) = \begin{bmatrix} \hat{x}(kT) \\ \hat{w}(kT) \end{bmatrix}$$

## Augmented System Model

**Augmented state equation:**

$$\hat{z}(kT+T) = \begin{bmatrix} G & I \\ 0 & 1 \end{bmatrix} \hat{z}(kT) + \begin{bmatrix} H \\ 0 \end{bmatrix} u(kT)$$

**Augmented output equation:**

$$\hat{y}(kT) = \begin{bmatrix} C & 0 \end{bmatrix} \hat{z}(kT)$$

## How It Works

1. The disturbance state $\hat{w}(kT)$ is treated as an additional state
2. The observer estimates both the system states and the disturbance
3. The estimated disturbance is subtracted from the control input for rejection
4. This provides integral-like action without explicitly adding an integrator state

## Alternative Approach

Alternatively, you can simply use $\hat{x}(kT)$ together with the dynamic extension (previously covered) to achieve integral action through the standard [[Integral Action]] augmentation method.

## Why Use This?

- Handles unknown constant or slowly-varying disturbances
- More general than standard integral action — can estimate time-varying disturbances
- Integrates naturally with observer-based control framework
- The [[Separation Principle]] still applies to the augmented system
