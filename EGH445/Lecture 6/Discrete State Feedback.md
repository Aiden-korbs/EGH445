# Discrete State Feedback

## Main Idea
- With a discrete-time state-space model, we can use **state feedback** to place closed-loop poles at chosen locations in the $z$-plane.

## Plant Model
The discrete plant is written as:
$$
x(kT+T)=Gx(kT)+Hu(kT)
$$
$$
y(kT)=Cx(kT)+Du(kT)
$$

## State Feedback Law
The lecture uses:
$$
u(kT)=r(kT)-Kx(kT)
$$
where
$$
K=\begin{bmatrix}k_0 & k_1 & \dots & k_{n-1}\end{bmatrix}
$$

## Closed-Loop Model
Substituting the control law:
$$
x(kT+T)=Gx(kT)+H\bigl(-Kx(kT)+r(kT)\bigr)
$$
so
$$
x(kT+T)=(G-HK)x(kT)+Hr(kT)
$$

The output remains:
$$
y(kT)=Cx(kT)+Du(kT)
$$

## Closed-Loop Matrix
- The key closed-loop state matrix is:
$$
G_{\text{cl}}=G-HK
$$

## Pole Placement Condition
- If the system is state controllable, the eigenvalues of $G-HK$ can be assigned to desired locations in the $z$-plane.

## Interpretation
- Continuous-time state feedback uses integration in the state model.
- Discrete-time state feedback replaces that with a **sample-to-sample delay**, often represented conceptually by $z^{-1}I$.

## Why It Matters
- This is the main control structure used for:
  - [[Regulation with Zero Reference]]
  - [[Regulation with Non-Zero Reference]]
  - [[Feedforward Gain for Reference Tracking]]

## Links
- [[Controllability]]
- [[State Feedback Design Procedure]]
- [[Pole Placement Gain Methods]]

## Visual Placeholders
![[Discrete State Feedback Architecture.png|400]]
