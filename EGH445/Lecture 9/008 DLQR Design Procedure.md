# DLQR Design Procedure

## Step-by-Step Design Process

The design of DLQR controllers follows these steps:

### Step 1: Check Controllability

Verify that the pair $(G, H)$ is controllable by checking the rank of the controllability matrix:

$$\mathcal{C} = [H, GH, G^2H, \dots, G^{n-1}H]$$

The system is controllable if $\text{rank}(\mathcal{C}) = n$.

### Step 2: Select Cost Matrices $Q \succeq 0$ and $R \succ 0$

Choose the state penalty matrix $Q$ and control penalty matrix $R$ to encode your performance preferences:

- Larger $Q$ relative to $R$ → faster state convergence, higher control effort
- Larger $R$ relative to $Q$ → slower state convergence, lower control effort
- Diagonal matrices are typical; off-diagonal terms can encode cross-penalties

$$J = \sum_{k=0}^{\infty} \left( x(kT)^\top Q x(kT) + u(kT)^\top R u(kT) \right)$$

### Step 3: Solve the DARE

Solve the Discrete Algebraic Riccati Equation for the unique symmetric positive semi-definite $P$:

$$P = G^\top P G - (G^\top P H)(R + H^\top P H)^{-1}(H^\top P G) + Q$$

### Step 4: Compute the Gain Matrix

$$K = (R + H^\top P H)^{-1} H^\top P G$$

### Step 5: Implement the Controller

$$u(kT) = -K x(kT)$$

The closed-loop system is:

$$x(kT + T) = (G - HK) x(kT)$$

### Step 6: Test and Adjust

Test the controller performance (simulation, step response, disturbance rejection). If performance is unsatisfactory:

- Adjust $Q$ and $R$ to change the trade-off
- Re-run from Step 3

## Practical Notes

- In MATLAB/Python, `scipy.linalg.solve_discrete_are()` solves the DARE
- Verify all closed-loop eigenvalues are inside the unit circle: $|\lambda_i(G - HK)| < 1$
- Check control signals for saturation or excessive magnitude
- For MIMO systems, $Q$ and $R$ may be block-diagonal to weight different states and inputs independently

## Key Takeaways

1. Check controllability
2. Select $Q \succeq 0$ and $R \succ 0$
3. Solve DARE for $P$
4. Compute $K = (R + H^\top P H)^{-1} H^\top P G$
5. Implement $u(kT) = -K x(kT)$
6. Test, iterate

## Related

- [[007 Discrete Linear Quadratic Regulator DLQR]]
- [[009 DLQR Stability Theorem]]
- [[010 DLQR Examples]]
- [[011 DLQR Tuning]]
