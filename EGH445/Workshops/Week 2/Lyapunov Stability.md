← Back to [[Week 2 Workshop]]

## Lyapunov Stability Criteria 
Lyapunov stability evaluates system stability by defining a positive definite "energy" function, $V(x)$, and observing its rate of change, $\dot{V}(x)$, over time .

* **Energy Function Setup:** $V(x) > 0$ for all $x \neq 0$, and $V(0) = 0$ .
* **Stability Conditions:**
    * **Stable (Lyapunov Stable):** If $\dot{V}(x) \le 0$, the system's energy is decreasing or constant, meaning it stays in a local region near the equilibrium point .
    * **Asymptotically Stable:** If $\dot{V}(x) < 0$, the system energy strictly decreases, guaranteeing it returns exactly to the equilibrium point ($x(t) \rightarrow 0$) .
    * **Unstable:** If $\dot{V}(x) > 0$, system energy is increasing .

### The Lyapunov Equation for LTI Systems
For an LTI system $\dot{x} = Ax$, we define a quadratic energy function using a symmetric positive definite matrix $P$: $$V(x) = x^T P x$$ The derivative is defined using another matrix $Q$: $$\dot{V}(x) = -x^T Q x$$ This relationship yields the **Lyapunov Equation**: $$A^T P + PA = -Q$$ 
* **Application:** A positive definite solution $P > 0$ (given a chosen positive definite $Q > 0$) exists if and only if all eigenvalues of $A$ have negative real parts .