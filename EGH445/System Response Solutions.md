← Back to [[Response and Stability]]

## Solving State-Space Models

### The General Problem 
To find the system response $x(t)$, we must solve the differential equation $\dot{x} = f(x,u)$ given an initial condition $x(t_0) = x_0$ . The general solution is expressed as an integral: $$x(t) = x(t_0) + \int_{t_0}^{t} f(x,u)dt$$ 
* For linear systems, this integral can be solved analytically .
* For nonlinear systems, this integral must be solved numerically .

### Analytical Solution for LTI Systems 
For a Linear Time-Invariant (LTI) system defined by $\dot{x} = Ax + Bu$ , the general analytical solution is: $$x(t) = e^{At}x_0 + \int_{0}^{t} e^{A(t-\tau)}Bu(\tau)d\tau$$ 
* **The Transition Matrix ($e^{At}$):** This matrix exponential governs the unforced, natural response of the system . It can be calculated using the inverse Laplace transform: $e^{At} = \mathcal{L}^{-1}\{(sI - A)^{-1}\}$ .
* **Similarity Transformations:** If the matrix $A$ is diagonalizable (has distinct eigenvalues), the transition matrix can be computed using a similarity transformation: $e^{At} = T e^{\Lambda t} T^{-1}$, where $T$ is the matrix of eigenvectors and $\Lambda$ is the diagonal matrix of eigenvalues .