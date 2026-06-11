# DLQR Stability Theorem

## Stability Questions

- Does a unique solution to the DARE always exist?
- Does the resulting controller guarantee stability?

## Conditions for Stabilizing DLQR Solution

Two conditions must be met:

1. **Controllability:** Can the controller move all unstable poles of the system?
2. **Observability:** Can all unstable modes be observed through the cost function?

Note: The observability condition is on the pair $(G, V)$ where $Q = V^\top V$, not on the system output matrix $C$. This is observability of the states by the cost function, not by the measurements.

## DLQR Stability Theorem

**Theorem:** Assume $R \succ 0$ and $Q \succeq 0$. Let $Q = V^\top V$ (where $V$ might not be unique).

If the following conditions hold:

1. The pair $(G, H)$ is **controllable**
2. The pair $(G, V)$ is **observable**

Then:

1. A unique solution $P = P^\top \succeq 0$ to the DARE exists
2. The resulting controller yields a **stable closed-loop system** (all eigenvalues of $G - HK$ lie strictly inside the unit circle)

## Observability Clarification

The observability condition uses $Q = V^\top V$, where the observability matrix is:

$$\mathcal{O} = \begin{bmatrix} V \\ VG \\ \vdots \\ VG^{n-1} \end{bmatrix}$$

This checks whether all states that contribute to the cost function can be "observed" through the cost. If a state is not penalised ($Q$ has zero rows/columns for that state) and is uncontrollable, the DARE solution may not be stabilising.

## Practical Implications

- In practice, choose $Q \succ 0$ (positive definite) to ensure all states are penalised, which guarantees observability of $(G, V)$
- If some states are intentionally not penalised, verify that the pair $(G, V)$ is observable
- Controllability of $(G, H)$ is essential — if the system is not controllable, no state-feedback law can place all poles

## Key Takeaways

- DLQR guarantees a unique DARE solution and closed-loop stability if $(G, H)$ is controllable and $(G, V)$ is observable
- Choosing $Q \succ 0$ (positive definite) is a safe practical choice
- The observability here is with respect to the cost function, not system outputs

## Related

- [[007 Discrete Linear Quadratic Regulator DLQR]]
- [[008 DLQR Design Procedure]]
- [[010 DLQR Examples]]
