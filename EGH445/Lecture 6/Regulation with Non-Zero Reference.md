# Regulation with Non-Zero Reference

## Main Idea
- Standard state feedback can place poles well, but it usually changes the system’s **steady-state gain**.
- That means a system can become well damped and stable while still failing to track a fixed non-zero command properly.

## Modified Architecture
To track a constant non-zero reference, the lecture introduces a **feedforward gain**:
$$
K_r
$$

The control architecture becomes:
$$
u(kT)=K_r\,r(kT)-Kx(kT)
$$

## Closed-Loop State Equation
Substituting into the plant gives:
$$
x(kT+T)=(G-HK)x(kT)+HK_r\,r(kT)
$$

## Design Logic
- Use $K$ to place the closed-loop poles where you want them in the $z$-plane.
- Use $K_r$ to adjust the steady-state gain so a fixed reference is tracked correctly.

## Key Insight
- Pole placement handles **transient dynamics**.
- Feedforward gain handles **steady-state scaling**.

## When This Applies
- Fixed or constant references
- Step-type reference tracking
- Cases where the steady-state error after state feedback alone is not acceptable

## Links
- [[Feedforward Gain for Reference Tracking]]
- [[Regulation with Zero Reference]]
- [[Discrete State Feedback]]

## Visual Placeholders
![[Non Zero Reference State Feedback.png|400]]
