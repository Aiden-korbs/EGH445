← Back to [[Response and Stability]]

## Energy-Based Stability Analysis
Lyapunov stability uses an artificial "energy" function, $V(x)$, to determine the stability of an equilibrium point without solving the differential equations.

* **Function Setup:** The energy function must be positive definite: $V(x) > 0$ for all $x \neq 0$, and $V(0) = 0$.
* **Stability Conditions:**
    * **Asymptotically Stable:** If the derivative $\dot{V}(x)$ is strictly negative ($\dot{V}(x) < 0$), system energy is always decreasing, and the states will return to the equilibrium point.
    * **Stable (Lyapunov Stable):** If $\dot{V}(x) \le 0$, energy is not increasing, and the system states will remain bounded near the equilibrium point.
    * **Unstable:** If $\dot{V}(x) > 0$ for any $x$, the energy is increasing, and the system is unstable.

### The Lyapunov Equation (LTI Systems)
For an LTI system $\dot{x} = Ax$, we construct a quadratic energy function using a symmetric, positive definite matrix $P$: $V(x) = x^T P x$.Taking the derivative yields: $\dot{V}(x) = x^T(A^T P + PA)x$.

By defining a positive definite matrix $Q$, we get the **Lyapunov Equation**:$$A^T P + PA = -Q$$
* **The Connection to Eigenvalues:** A positive definite solution $P$ exists (given a positive definite $Q$) if, and only if, all eigenvalues of $A$ have strictly negative real parts ($Re(\lambda_i) < 0$).