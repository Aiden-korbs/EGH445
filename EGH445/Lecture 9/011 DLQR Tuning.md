# DLQR Tuning

## The Trade-off

The relative size of the cost matrices ($Q/R$ ratio) directly affects the trade-off between state regulation and control effort.

## Tuning Guidelines

### Increasing $Q$ Relative to $R$

Increasing the state penalty $Q$ while keeping $R$ fixed (or increasing $Q$ faster than $R$):

- **Increases the penalty on state deviation**
- Results in faster state convergence
- Requires higher control effort

### Increasing $R$ Relative to $Q$

Increasing the control penalty $R$ while keeping $Q$ fixed (or increasing $R$ faster than $Q$):

- **Increases the penalty on control effort**
- Results in slower state convergence
- Requires lower control effort

## Tuning Matrix Structure

The individual weights $q_{i,j}$ and $r_{i,j}$ in the cost matrices can be tuned independently:

$$Q = \begin{bmatrix} q_{1,1} & q_{1,2} \\ q_{2,1} & q_{2,2} \end{bmatrix}, \quad R = \begin{bmatrix} r_{1,1} & r_{1,2} \\ r_{2,1} & r_{2,2} \end{bmatrix}$$

- Diagonal weights penalise individual states/inputs
- Off-diagonal weights penalise cross-terms between states/inputs
- Common practice: start with diagonal $Q$ and $R$, then adjust based on simulation

## Tuning Procedure

1. Start with initial $Q \succeq 0$ and $R \succ 0$
2. Solve the DARE and compute $K$
3. Simulate the closed-loop system
4. Evaluate:
   - Are state responses acceptable (settling time, overshoot)?
   - Are control signals within feasible ranges?
5. Adjust $Q$ and/or $R$:
   - States settle too slowly → increase corresponding diagonal elements of $Q$
   - Control effort too large → increase corresponding diagonal elements of $R$
   - Excessive cross-coupling → add off-diagonal terms
6. Iterate until satisfactory performance

## Key Takeaways

- $Q/R$ ratio encodes the performance trade-off
- Larger $Q/R$ → aggressive control (fast states, high effort)
- Smaller $Q/R$ → conservative control (slow states, low effort)
- Tuning is iterative: simulate, evaluate, adjust, repeat

## Related

- [[006 Optimal Control Fundamentals]]
- [[007 Discrete Linear Quadratic Regulator DLQR]]
- [[008 DLQR Design Procedure]]
- [[012 LQR Limitations and Control Saturation]]
