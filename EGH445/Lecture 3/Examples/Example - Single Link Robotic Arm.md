← Back to [[Nonlinear Systems and Linearisation]]
## Scenario
Linearise a single link robotic arm about its equilibrium points and analyse system stability.

## Given
*$\dot{x}_1 = x_2$*$\dot{x}_2 = -\frac{g}{l}\sin(x_1) - \frac{b}{ml^2}x_2 + T$*Assumptions: Mass $m=1$, input torque $T(t) = u(t)$, arm is rigid.

## Steps
**1. Find Equilibrium Points**:
* Solve $0 = f(\overline{x})$.
* EP 1 (Hanging down): $\overline{x}^1 = [0, 0]^T, \overline{u}^1 = 0$.
* EP 2 (Pointing up): $\overline{x}^2 = [\pi, 0]^T, \overline{u}^2 = 0$.
* EP 3 (Arbitrary Angle $q^*$): requires steady-state forced input $\overline{u}^3 = \frac{g}{l}\sin(q^*)$.

**2. Evaluate Jacobians (for A and B matrices)**:
* $A = \begin{bmatrix} 0 & 1 \\ -\frac{g}{l}\cos(x_1) & -\frac{b}{ml^2} \end{bmatrix}$.
* $B = \begin{bmatrix} 0 \\ 1 \end{bmatrix}$.

**3. Test Stability via Eigenvalues**:
* Assuming system parameters ($m=0.5, b=0.3, l=0.4, g=9.8$).
* For EP 1 (Hanging): $\lambda^1 = -1.88 \pm 4.58j$ $\rightarrow$ **Stable**.
* For EP 2 (Upright): $\lambda^2 = 3.42, -7.17$ $\rightarrow$ **Unstable (Saddle point)**.
* For EP 3 (at $45^\circ / \pi/4$): $\lambda^3 = -1.88 \pm 3.72j$ $\rightarrow$ **Stable** .

## Final Notes
* The A and B matrices form fixed scalar values specific to the chosen equilibrium point.
* Applying open loop unforced control results in the system settling near the stable hanging equilibrium point.
* Applying a steady-state forced torque results in settling near the targeted angle.