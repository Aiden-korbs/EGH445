# DLQR Examples

## Scalar DLQR Example

### System

Consider the scalar system with cubic nonlinearity and its discrete linearised version:

$$\dot{x}(t) = -x(t) + x(t)^3 + u(t) \quad \rightarrow \quad x(kT + T) = 0.905x(kT) + 0.095u(kT)$$

with $T = 0.1\,\text{s}$, $G = 0.905$, $H = 0.095$.

### Step 1: Controllability

$$\mathcal{C} = [H] = [0.095]$$

Full rank ($\text{rank}(\mathcal{C}) = 1$). The system is controllable.

### Step 2: Cost Matrices

Select:

$$Q = 10.0, \quad R = 0.1$$

### Step 3: Observability

$$V = \sqrt{Q} = \sqrt{10} = 3.162$$

$$\mathcal{O} = \begin{bmatrix} V \\ VG \end{bmatrix} = \begin{bmatrix} 3.162 \\ 3.162 \times 0.905 \end{bmatrix} = \begin{bmatrix} 3.162 \\ 2.857 \end{bmatrix}$$

Full rank. The pair $(G, V)$ is observable.

### Step 4: Solve the DARE

For the scalar case, the DARE simplifies to a quadratic equation:

$$P - G^2 P + \frac{G^2 H^2 P^2}{R + H^2 P} = Q$$

Rearranging:

$$(H^2)P^2 + (R - G^2 R - QH^2)P + (-QR) = 0$$

Substituting values:

$$0.009P^2 - 0.0722P - 1 = 0$$

Solving:

$$P = 15.2571 \quad \text{or} \quad P = -7.2624$$

Pick the positive semi-definite solution: $P = 15.2571$.

### Step 5: Compute the Gain

$$K = (R + H^\top P H)^{-1} H^\top P G = (0.1 + 0.095^2 \times 15.2571)^{-1} \times 0.095 \times 15.2571 \times 0.905 = 5.519$$

### Result

| Quantity | Value |
|---|---|
| $P$ (DARE solution) | 15.2571 |
| $K$ (DLQR gain) | 5.519 |
| Closed-loop pole | $G - HK = 0.905 - 0.095 \times 5.519 = 0.381$ |
| Stability | Stable ($|0.381| < 1$) |

Compare with the pole placement gain $K_{PP} = 4.263$ — the DLQR gain is larger because it balances state regulation against control effort via the cost function.

## MIMO DLQR Example

### System

Consider the MIMO system with two states and two inputs:

$$x(kT + T) = \begin{bmatrix} 1 & 0.1 \\ 0 & 0.8 \end{bmatrix} x(kT) + \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix} u(kT)$$
$$y(kT) = C x(kT) + D u(kT)$$

### Comparison with Pole Placement

Pole placement for this MIMO system was underdetermined (2 equations, 4 unknowns). DLQR provides a unique, systematic solution.

For the same system, different DLQR designs yield unique gains. For example:

$$K_3 = \begin{bmatrix} 0.990 & 0.099 \\ 0.000 & 0.792 \end{bmatrix}$$

with closed-loop eigenvalues:

$$\lambda(G - HK_3) = \begin{bmatrix} 0.0098, & 0.0079 \end{bmatrix}$$

All eigenvalues are well inside the unit circle, indicating excellent stability margins.

## Key Takeaways

- The scalar DLQR example shows the DARE reduces to a quadratic equation in the scalar case
- DLQR produces a unique gain even when pole placement has degrees of freedom (MIMO case)
- The MIMO DLQR example demonstrates eigenvalues pushed very close to the origin for fast convergence
- DLQR handles multi-variable systems naturally without eigenvector ambiguity

## Related

- [[007 Discrete Linear Quadratic Regulator DLQR]]
- [[008 DLQR Design Procedure]]
- [[009 DLQR Stability Theorem]]
- [[011 DLQR Tuning]]
