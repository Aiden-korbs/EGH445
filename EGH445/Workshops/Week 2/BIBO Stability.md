← Back to [[Week 2 Workshop - System Response and Stability]]

# BIBO Stability
**Bounded-Input Bounded-Output Stability**

## Definition
A (SISO) LTI system is **BIBO stable** if and only if, for **every bounded input** $u(t)$, the **output** $y(t)$ is bounded.

$$\|u(t)\| \leq K_u < \infty \implies \|y(t)\| \leq K_y < \infty$$

> Also called **external stability**.

## Transfer Function Form

$$H(s) = \frac{P(s)}{Q(s)}, \quad Q(s) = (s - p_1)(s - p_2)(s - p_3) \cdots (s - p_n)$$

## Stability Condition
$H(s)$ is BIBO stable **if and only if** all its **poles have negative real parts**:

$$\text{Re}(p_i) < 0 \quad \forall \; i$$

In the $s$-plane: $s = \sigma + j\omega$, all poles must lie in the **left-half plane (LHP)**.

![[BIBO Stability Pole Plot.png|400]]

## Comparison with Internal Stability

| Property | BIBO Stability | [[Internal Stability]] |
| :--- | :--- | :--- |
| Type | External | Internal |
| Condition | All poles in LHP | All eigenvalues of $A$ in LHP |
| Scope | Input-output behaviour | All internal states |
| Strength | Weaker | **Stronger** |

> **Note:** Pole-zero cancellation is only mathematical — the pole still physically exists. Internal states tied to that pole may be unstable even if BIBO stability appears satisfied.

## Related Notes
- [[Internal Stability]]
- [[State Transition Matrix]]
