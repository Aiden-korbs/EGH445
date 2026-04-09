# Direct Discrete Design Workshop View

## Direct Approach
- The workshop presents the direct workflow as:
  - **Real System**
  - $\rightarrow$ **Continuous Model**
  - $\rightarrow$ **Discrete Model**
  - $\rightarrow$ **Discrete Controller**

## Design Options
- At least two controller design paths are highlighted:
  - **State feedback**
  - **Classical discrete design methods**

## State Feedback Structure
- The control law is based on a gain vector $K$.
- For regulation, the controller is commonly written as:
$$
u(k) = -Kx(k)
$$
- With a reference input present, the workshop later extends this to include a feedforward term.

## Closed-Loop Structure
- The workshop diagram uses:
  - state matrix $G$
  - input matrix $H$
  - output matrix $C$
  - direct term $D$
  - a discrete delay block $z^{-1}I$

## Practical Interpretation
- State feedback allows the designer to **place closed-loop poles**.
- This is how discrete design is tied to performance goals such as:
  - rise time
  - overshoot
  - damping
  - settling time

## Links
- [[Regulation in Discrete Control]]
- [[Aircraft State Feedback Design]]
- [[Week 6 Lecture Highlights]]

## Visual Placeholders
![[Direct Design State Feedback Structure.png|400]]
