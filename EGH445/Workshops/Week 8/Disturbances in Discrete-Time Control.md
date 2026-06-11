# Disturbances in Discrete-Time Control

## Core Idea
- A controller may perform well for regulation, but **input disturbances** can still shift the output away from the target.
- A disturbance enters the dynamics through a disturbance input matrix.

## Disturbed Closed-Loop Model
$$
x(kT+T) = (G - HK)x(kT) + H_d d(kT)
$$

$$
y(kT) = Cx(kT) + Du(kT)
$$

- Here:
  - $x \in \mathbb{R}^n$
  - $u \in \mathbb{R}^m$
  - $d \in \mathbb{R}^l$
  - $H_d \in \mathbb{R}^{n \times l}$

## Feedforward Rejection Idea
- If the disturbance is known exactly, a feedforward term can be added:
$$
u(kT) = -Kx(kT) + u_{ff}
$$

- With ideal cancellation:
$$
u_{ff} = -\hat{H}^{-1}\hat{H}_d d(kT)
$$

## Practical Limitation
- This only works well if:
  - the disturbance is known
  - the plant model is accurate
  - the matrices used in the controller match the real system

## Practical Takeaway
- If $H$, $G$, $H_d$, or $d(kT)$ are uncertain, feedforward compensation can fail.

## Links
- [[Integral Action in Discrete-Time Control]]
- [[Tracking and Internal Model Principle]]

## Visual Placeholders
![[Disturbance Feedforward Comparison.png|400]]
