# Discrete Linear Quadratic Regulator (DLQR)

## Formulation

The **Discrete Linear Quadratic Regulator (DLQR)** is the optimal state-feedback controller that minimises the infinite-horizon quadratic cost function subject to discrete-time linear system dynamics.

## Cost Function

$$J = \sum_{k=0}^{\infty} \left( x(kT)^\top Q x(kT) + u(kT)^\top R u(kT) \right)$$

where:

- $Q \succeq 0$ — state penalty matrix (positive semi-definite)
- $R \succ 0$ — control penalty matrix (positive definite)
- Infinite horizon: the sum extends from $k = 0$ to $\infty$

## Optimal Control Law

The optimal control input is a linear state-feedback law:

$$u(kT) = -K x(kT)$$

## Control Gain

The gain matrix $K$ is:

$$K = (R + H^\top P H)^{-1} H^\top P G$$

where $P$ is the unique, symmetric, positive semi-definite solution of the DARE.

## Discrete Algebraic Riccati Equation (DARE)

$$P = G^\top P G - (G^\top P H)(R + H^\top P H)^{-1}(H^\top P G) + Q$$

$P$ must satisfy:

- $P = P^\top$ (symmetric)
- $P \succeq 0$ (positive semi-definite)

The closed-loop system matrix is:

$$A_{cl} = G - HK$$

and the closed-loop dynamics are:

$$x(kT + T) = (G - HK) x(kT)$$

## Closed-Loop Stability

Under the conditions of the DLQR Stability Theorem, the closed-loop system is guaranteed to be stable (all eigenvalues of $G - HK$ lie strictly inside the unit circle).

## Derivation Note

The full derivation of the optimal control gain $K$ formula is based on Bellman's Principle of Optimality (Dynamic Programming), which is beyond the scope of this course.

## Key Takeaways

- DLQR solves the infinite-horizon optimal control problem for discrete-time linear systems
- The optimal gain $K$ is computed from the DARE solution $P$
- $Q$ penalises state deviations; $R$ penalises control effort
- Under controllability/observability conditions, the closed-loop system is stable

## Related

- [[006 Optimal Control Fundamentals]]
- [[008 DLQR Design Procedure]]
- [[009 DLQR Stability Theorem]]
- [[010 DLQR Examples]]
