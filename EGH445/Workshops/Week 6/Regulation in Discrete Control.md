# Regulation in Discrete Control

## Zero Reference
- For **zero-reference regulation**, the design focus is disturbance rejection and state decay back to equilibrium.
- The workshop shows the controller in the form:
$$
u(k) = -Kx(k)
$$
- This creates a closed-loop plant with no explicit reference feedforward path.

## Non-Zero Reference
- For **non-zero reference regulation**, a fixed reference is introduced.
- The workshop notes that an additional gain $K_r$ is used so the system regulates to:
$$
r(k) = \kappa
$$
for a constant target.

## Design Steps for Zero Reference
1. Check controllability and observability.
2. Define the control objective and performance specifications.
3. Find desired poles $z^\ast$.
4. Form the desired closed-loop characteristic equation.
5. Choose a design method:
   - equating coefficients
   - phase variable form
   - transforms
6. Solve for the feedback gain $K$ and implement:
$$
u(k) = -Kx(k)
$$

## Additional Steps for Non-Zero Reference
7. Define the required reference value $r(k)=\kappa$.
8. Construct the closed-loop system with $K_r$.
9. Use the pulse transfer function and final value theorem to solve for the feedforward gain $K_r$.

## Practical Notes
- The reference can be any fixed value.
- If the reference changes, then $K_r$ may need to change accordingly.
- The feedback gain $K$ determines the closed-loop dynamics.
- The gain $K_r$ is used to achieve the desired steady-state output level.

## Links
- [[Direct Discrete Design Workshop View]]
- [[Aircraft State Feedback Design]]

## Visual Placeholders
![[Zero Reference Structure.png|400]]
![[Non Zero Reference Structure.png|400]]
