# LQR Limitations and Control Saturation

## LQR Limitations

The Linear Quadratic Regulator may not be suitable for all systems. Key limitations include:

- **Control saturation:** LQR does not explicitly handle input constraints
- **Model accuracy:** LQR performance depends on the accuracy of the linearised model
- **Nonlinear systems:** LQR is designed for linear systems and may fail on strongly nonlinear dynamics

## Control Saturation Example

Consider the second-order system:

$$\ddot{x} = x - c\dot{x} + u$$

where the control input is constrained:

$$u_{\min} \leq u(kT) \leq u_{\max}$$

## Three Approaches Compared

| Approach | Constraints | Method |
|---|---|---|
| Unconstrained LQR | None | Standard LQR design, no saturation applied |
| Saturated LQR | $u_{\min} \leq u(kT) \leq u_{\max}$ | LQR designed without constraints, then actuator saturation applied in simulation |
| MPC | $u_{\min} \leq u(kT) \leq u_{\max}$ | LQR with a prediction horizon that explicitly handles constraints via optimisation |

## Unconstrained LQR

- LQR gain is computed without considering saturation limits
- The controller assumes unlimited control authority
- Results in fast response and small tracking error in simulation (idealised)
- In practice, the actuator cannot deliver the required control signal

## Saturated LQR

- Same LQR gain as unconstrained case
- Control effort is clamped to $[u_{\min}, u_{\max}]$ at each time step
- Consequences:
  - Actuator saturation causes integrator windup-like behaviour
  - State may diverge or oscillate
  - Performance degrades significantly when the required control exceeds limits
  - The closed-loop stability guarantees of LQR no longer hold when saturation is active

## Why Saturated LQR Fails

When the control signal saturates:

- The actual applied input differs from the designed $u(kT) = -Kx(kT)$
- The closed-loop dynamics no longer match $(G - HK)$
- The system may exhibit limit cycles, slow recovery, or instability
- The linear analysis and stability guarantees are invalidated

## Key Takeaways

- LQR assumes unlimited control authority — real actuators have limits
- Saturated LQR applies a hard clamp that breaks the stability guarantees
- When constraints are important, consider MPC which handles them explicitly in the optimisation
- For LQR to work well, the operating region must be small enough that saturation rarely occurs

## Related

- [[005 Pole Placement Control Effort Trade-offs]]
- [[006 Optimal Control Fundamentals]]
- [[011 DLQR Tuning]]
- [[013 Model Predictive Control MPC]]
