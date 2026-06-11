# Integral Action for Disturbance Rejection

## Main Idea
- Integral action is introduced so the controller can remove steady-state error caused by constant disturbances.
- In classical terms, this makes the loop behave like a **Type 1** system for step-like effects.

## Integral State
- Introduce a new state $q$ that integrates the output or error.
- For the zero-reference disturbance-rejection case:
$$
q(kT+T) = q(kT) + y(kT)
$$

## Control Law
$$
u(kT) = -K_x x(kT) - K_I q(kT)
$$

## Why It Works
- If a constant disturbance pushes the output away from zero, the integral state accumulates that error.
- The accumulated value changes the input until the steady-state output is driven back toward zero.

## Important Insight
- Integral action does not require exact knowledge of the disturbance magnitude.
- It uses the **observed error** rather than explicit disturbance measurement.

## Trade-Offs
- Better steady-state rejection
- Increased controller order
- Possible slower or more oscillatory transients if poles are poorly chosen

## Links
- [[Augmented System for Integral Action]]
- [[Non-Zero Regulation with Integral Action]]
- [[Internal Model Principle]]

## Visual Placeholders
![[Integral Action Block Diagram.png|400]]
