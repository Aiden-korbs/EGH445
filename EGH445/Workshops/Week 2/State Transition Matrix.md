← Back to [[Week 2 Workshop - System Response and Stability]]

# State Transition Matrix

## Definition
- The **matrix exponential** $e^{At}$ is called the **state transition matrix**.
- It describes how the state transitions over time in a linear system.

## Power Series Representation

$$e^{At} = \sum_{k=0}^{\infty} \frac{1}{k!} A^k t^k = I + At + \frac{1}{2!}A^2t^2 + \cdots$$

## Methods to Compute $e^{At}$

| Method | Formula | Notes |
| :--- | :--- | :--- |
| **Power Series** | $I + At + \frac{1}{2!}A^2t^2 + \cdots$ | Approximation |
| **Laplace Transform** | $e^{At} = \mathcal{L}^{-1}\{(sI - A)^{-1}\}$ | Exact |
| **Eigendecomposition** | $e^{At} = T \, \text{diag}(e^{\lambda_i t}) \, T^{-1}$ | Only when $A$ is **diagonalisable** (unique eigenvalues) |

## Eigendecomposition Form

$$e^{At} = T \begin{bmatrix} e^{\lambda_1 t} & 0 & \cdots & 0 \\ 0 & e^{\lambda_2 t} & & \vdots \\ \vdots & & \ddots & \\ 0 & \cdots & & e^{\lambda_n t} \end{bmatrix} T^{-1}$$

- $T = [V_1 \; V_2 \; \cdots]$ where $V_i$ are the **eigenvectors** of $A$
- $\lambda_n$ are the **eigenvalues** of $A$

## Key Properties

| Property | Expression |
| :--- | :--- |
| Identity at $t=0$ | $e^{0} = I$, where $I, 0 \in \mathbb{R}^{n \times n}$ |
| Transpose | $e^{M^T} = (e^M)^T$ |
| Derivative | $\frac{d}{dt} e^{At} = A e^{At} = e^{At} A$ |

## Related Notes
- [[Analytical Solution - Linear Systems]]
- [[Internal Stability]]
- [[Lyapunov Stability]]
