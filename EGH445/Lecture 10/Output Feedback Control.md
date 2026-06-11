# Output Feedback Control

← Back to [[State Estimation: Observers and Output Feedback]]

## Concept

Combines state-feedback controller with state observer. Since $x(kT)$ is not directly measured, we use $\hat{x}(kT)$ from the observer in the control law.

## Structure

**Observer:**

$$\hat{x}(kT+T) = (G - LC)\hat{x}(kT) + Hu(kT) + Ly(kT)$$

**Control Law:**

$$u(kT) = -K\hat{x}(kT)$$

| Symbol | Role |
|--------|------|
| $K$ | State-feedback gain (designed assuming $x(kT)$ available) |
| $L$ | Observer gain |

## Closed-Loop Dynamics

State variables: actual state $x(kT)$ and estimation error $e(kT) = x(kT) - \hat{x}(kT)$.

$$u(kT) = -K\hat{x}(kT) = -K(x(kT) - e(kT))$$

Substituting into the state equation:

$$x(kT+T) = Gx(kT) - HKx(kT) + HKe(kT)$$
$$x(kT+T) = (G - HK)x(kT) + HKe(kT)$$

Combined in matrix form:

$$\begin{bmatrix} x(kT+T) \\ e(kT+T) \end{bmatrix} = \begin{bmatrix} G - HK & HK \\ 0 & G - LC \end{bmatrix} \begin{bmatrix} x(kT) \\ e(kT) \end{bmatrix}$$

## Key Insight

The closed-loop system matrix is **block upper triangular**, meaning its eigenvalues are the union of:

- Eigenvalues of $(G - HK)$ — determined by controller gain $K$
- Eigenvalues of $(G - LC)$ — determined by observer gain $L$

This leads to the [[Separation Principle]] and [[Certainty Equivalence Principle]].

## Design Implications

- Controller and observer can be designed **independently**
- The [[Separation Principle]] guarantees that the combined closed-loop eigenvalues are simply the union of controller and observer eigenvalues
- The [[Certainty Equivalence Principle]] states we use the same $K$ as if full state were available

## Observer Design Considerations

| Factor | Trade-off |
|--------|-----------|
| Speed | Faster convergence requires poles closer to origin |
| Noise | Large observer gains amplify measurement noise |
| Robustness | Need to balance performance with noise sensitivity |

Optimal observer design (e.g., [[Kalman Filter]]) explicitly addresses this trade-off. For pole placement, choose poles that are fast enough but not excessively so.
