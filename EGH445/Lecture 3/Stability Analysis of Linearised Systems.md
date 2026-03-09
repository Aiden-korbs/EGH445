← Back to [[Nonlinear Systems and Linearisation]]
## Global vs Local Stability
* Mathematical tools for linear systems can be applied identically to the linearised incremental model $\dot{\delta x} = A\delta x + B\delta u$.
* However, because it is an approximation, the stability results are strictly **local** (valid only near the equilibrium point) rather than global.

## Lyapunov's Indirect (1st) Method
* This method evaluates stability by analysing the **eigenvalues** ($\lambda_i$) of the Jacobian matrix $A$.
* Solved via characteristic equation: $\det(\lambda I - A) = 0$.
* The equilibrium point is (asymptotically) stable if the real parts of all eigenvalues are strictly negative: $Re(\lambda_i) < 0 \forall i$.
* See [[Eigenvalues and System Response Types]] for specific trajectory behaviours.

## Lyapunov's Direct (2nd) Method
* Relies on finding a scalar energy function $V(x)$.
* Requires $V(x) > 0$ for $x \neq 0$, and $V(0) = 0$.
* The system is locally stable if energy decreases over time: $\dot{V}(x) < 0$.