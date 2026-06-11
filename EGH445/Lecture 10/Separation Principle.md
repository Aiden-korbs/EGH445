# Separation Principle

← Back to [[State Estimation: Observers and Output Feedback]]

## Statement

When an observer-based controller is used ($u(kT) = -K\hat{x}(kT)$), the **controller design** and **observer design** can be performed independently.

## Mathematical Basis

From the combined closed-loop dynamics:

$$\begin{bmatrix} x(kT+T) \\ e(kT+T) \end{bmatrix} = \begin{bmatrix} G - HK & HK \\ 0 & G - LC \end{bmatrix} \begin{bmatrix} x(kT) \\ e(kT) \end{bmatrix}$$

The system matrix is **block upper triangular**. Therefore, its eigenvalues are the union of the diagonal blocks:

- $\text{eig}(G - HK)$ — controller poles
- $\text{eig}(G - LC)$ — observer error poles

## Certainty Equivalence Principle

Because the eigenvalues separate:

- The controller uses the **same gain $K$** as designed under the assumption that $x(kT)$ is fully available
- The observer uses gain $L$ designed independently to make $\hat{x}(kT) \to x(kT)$ quickly
- We treat the estimated state $\hat{x}(kT)$ as if it were the true state $x(kT)$

## Design Workflow

1. Design $K$ using pole placement or LQR, assuming full state feedback
2. Design $L$ using pole placement or LQE, ensuring observer poles are faster than controller poles
3. Combine: implement $u(kT) = -K\hat{x}(kT)$ with the observer dynamics

## Observer Pole Placement Rule of Thumb

Observer poles should be placed **5–10 times faster** (closer to the origin) than controller poles. This ensures:

- State estimates converge before the controller acts significantly
- The [[Certainty Equivalence Principle]] is effectively valid
