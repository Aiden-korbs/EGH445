# LQR Limitations

## Model Accuracy Dependency

- LQR performance relies on an accurate **linear model** (G, H).
- Nonlinearities or parameter uncertainties can degrade performance or lead to instability.

## Constraint Handling

- Standard LQR formulation does **not explicitly handle constraints** on states (x) or inputs (u).
- Example: **Actuator saturation** ($u_{min}\leq u(kT)\leq u_{max}$).
- Calculating gain K and then saturating the control value can lead to poor performance or instability.

## Implicit Pole Placement

- LQR does place closed-loop poles, but **indirectly** through the choice of Q and R.
- It's hard to directly relate Q/R choices to transient response characteristics (like %OS, t_s).

## Addressing Limitations

- For constraints: **Model Predictive Control (MPC)** explicitly incorporates constraints in its optimization.
