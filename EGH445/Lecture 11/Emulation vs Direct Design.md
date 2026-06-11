# Emulation vs Direct Design

## Emulation

Design a digital controller G_d(z) that mimics the behaviour of a pre-designed continuous controller G_c(s).

### Why Emulate?

- Leverage existing continuous controller designs
- Control design is sometimes preferred in the s-domain
- Implement advanced continuous controllers digitally

## Direct Design vs Emulation

| Aspect | Direct Design | Emulation |
|---|---|---|
| Approach | Discretise the plant, then design the controller directly (e.g., DLQR) | Design the controller in continuous domain (e.g., PID, Lead-Lag, LQR), then discretise it |
| Design domain | Discrete-time (z-domain) | Continuous-time (s-domain) $\rightarrow$ discrete-time (z-domain) |
| When used | When plant is inherently digital or discrete model is accurate | When continuous controller already exists or design is preferred in s-domain |
| Examples | DLQR, discrete pole placement | Discretised PID, discretised lead compensator |

## Three Discretisation Methods Overview

1. **Tustin (Bilinear) Transformation** — Uses trapezoidal integration for a bilinear relation between s and z
2. **Zero-Order Hold (ZOH) Equivalence** — Assumes input to the controller is held constant between samples
3. **Matched Pole-Zero (MPZ) Method** — Maps poles and zeros of G_c(s) to G_d(z) using z = e^{sT}
