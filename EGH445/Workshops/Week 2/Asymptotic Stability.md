← Back to [[Week 2 Workshop - System Response and Stability]]

# Asymptotic Stability

## Definition
**Asymptotic stability** means the system **returns to the equilibrium point**:

$$x(t) \to 0 \quad \text{as} \quad t \to \infty$$

> Stronger than [[Lyapunov Stability]], which only requires the state to remain nearby.

## Stability Classification Summary

| Type | Condition | Behaviour |
| :--- | :--- | :--- |
| **Lyapunov Stable** | $\dot{V}(x) \leq 0$, $Q \geq 0$ | $\text{Re}(\lambda_i) \leq 0$; stays near equilibrium |
| **Asymptotically Stable** | $\dot{V}(x) < 0$, $Q > 0$ | $\text{Re}(\lambda_i) < 0$; converges to equilibrium |
| **Unstable** | $\dot{V}(x) > 0$ | States diverge |

## Lyapunov Equation Condition
Using the [[Lyapunov Stability]] framework with $V(x) = x^T P x$:

$$A^T P + P A = -Q$$

A **positive definite solution** $P \succ 0$ exists (given $Q \succ 0$) **if and only if** all eigenvalues of $A$ have **negative real parts** — confirming asymptotic stability.

## Eigenvalue Interpretation
The eigenvalues $\lambda_i$ of $A$ are directly linked to $P$, $Q$, and $V$:
- They determine the specific stability class.
- Computed via: `eig(A)` in MATLAB.

## MATLAB — Lyapunov Analysis
```matlab
Q = eye(4);
P = lyap(A, Q);          % Solve Lyapunov equation

% Compute V(x) along trajectory
V = zeros(length(tOut), 1);
for k = 1:length(tOut)
    V(k) = x(k,:) * P * x(k,:)';   % V = x'Px
end
plot(tOut, V, 'LineWidth', 1.5);
```

## Related Notes
- [[Lyapunov Stability]]
- [[Internal Stability]]
- [[BIBO Stability]]
- [[B747 Aircraft Model - 6DOF]]
