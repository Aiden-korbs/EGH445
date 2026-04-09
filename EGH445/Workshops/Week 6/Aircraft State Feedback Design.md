# Aircraft State Feedback Design

## Design Method
- Because the aircraft model is higher order, the workshop recommends:
  - **transform methods**
  - or **software tools**
- MATLAB is shown using the `place` command:
$$
K = \mathrm{place}(G,H,\text{desired poles})
$$

## Example Gain
- For the **well damped** design case, the workshop gives:
$$
K = \begin{bmatrix}
0.0802 & 0.0077 & -10.1355 & -9.2758
\end{bmatrix}
$$

## Why Software Is Preferred
- Higher-order systems make manual coefficient matching harder.
- State-feedback software is efficient once:
  - the model is known
  - controllability is verified
  - desired poles are selected

## General Workflow
1. Obtain the discrete aircraft model.
2. Check controllability.
3. Select desired pole locations from performance goals.
4. Compute $K$ using transform methods or software.
5. Simulate the closed-loop system.

## Scenario
### Scenario
Design a state-feedback controller for the discretised aircraft model.

### Given
- Discrete matrices $G$ and $H$
- Desired discrete pole locations
- Verified controllability

### Steps
1. Build the discrete-time state-space model.
2. Confirm:
$$
\operatorname{rank}(\mathcal{C}_{GH}) = n
$$
3. Choose the desired closed-loop poles.
4. Compute the feedback gain using:
$$
K = \mathrm{place}(G,H,\text{desired poles})
$$
5. Implement the control law:
$$
u(k) = -Kx(k)
$$
6. Evaluate the closed-loop response.

### Final Notes
- The workshop uses this as the applied version of the direct discrete design ideas from lecture.

## Links
- [[Direct Discrete Design Workshop View]]
- [[Aircraft Performance Objectives]]
- [[Aircraft Response Evaluation]]

## Visual Placeholders
![[Aircraft State Feedback Gain.png|400]]
