# Aircraft Longitudinal Model

## Modelling Assumptions
- Aircraft motion is considered near:
  - **straight and level flight**
  - **constant velocity**
- The system is **linearised** about this equilibrium point.

## Incremental Longitudinal Model
- The longitudinal model describes changes in:
  - forward velocity $u$
  - upward velocity $w$
  - pitch angle $\theta$
  - pitch rate $q = \dot{\theta}$

## Continuous-Time Interpretation
- As pitch changes, the aircraft may:
  - descend and speed up
  - climb and slow down
- This appears as an **oscillatory motion**.

## Discrete Model Setup
- The workshop then uses a discretised version of the linearised system with sample time:
$$
T = 0.01
$$
- The thrust input is assumed zero:
$$
\delta_T = 0
$$
- Control is applied using the **elevator**:
$$
\delta_e
$$

## State Meaning
- The state vector corresponds to longitudinal motion variables:
$$
x(k) = \begin{bmatrix}
\Delta u(k) \\
\Delta w(k) \\
\Delta q(k) \\
\Delta \theta(k)
\end{bmatrix}
$$

## Notes
- The workshop explicitly says the example only uses forces along the body-frame $x$ axis to build the example.
- The same procedure would be repeated on the other axes and moments to create the full aircraft model.

## Links
- [[6DOF Aircraft Running Example]]
- [[Aircraft State and Motion Variables]]
- [[Aircraft State Feedback Design]]

## Visual Placeholders
![[Aircraft Linearisation Assumptions.png|400]]
![[Discrete Longitudinal Model.png|400]]
