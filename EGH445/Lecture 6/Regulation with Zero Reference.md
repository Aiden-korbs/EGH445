# Regulation with Zero Reference

## Meaning
- A **zero-reference regulation problem** sets:
$$
r(kT)=0
$$
- The controller aims to drive the state and output toward zero.

## Starting Control Law
From [[Discrete State Feedback]]:
$$
u(kT)=r(kT)-Kx(kT)
$$

With zero reference:
$$
u(kT)=-Kx(kT)
$$

## Closed-Loop Dynamics
The state equation becomes:
$$
x(kT+T)=(G-HK)x(kT)
$$

## Closed-Loop Poles
- The open-loop poles are the eigenvalues of $G$.
- The closed-loop poles are the eigenvalues of:
$$
G-HK
$$

## Why This Version Matters
- This is the basic pole-placement problem.
- Once this is solved, it becomes easier to extend to [[Regulation with Non-Zero Reference]].

## Design Focus
- Make the closed-loop poles:
  - stable, so $|z_i|<1$
  - fast enough for the desired transient response
  - sufficiently damped to control overshoot

## Practical View
- Zero-reference regulation is the cleanest setting for understanding:
  - controllability
  - pole placement
  - gain design
  - transformed state-space forms

## Links
- [[Discrete State Feedback]]
- [[State Feedback Design Procedure]]
- [[Pole Placement Gain Methods]]
