# Controllability and Observability Workshop View

## Controllability
- **Controllability** asks whether the available inputs are enough to move the system state where you want.
- Practical meaning:
  - can a controller exist for the chosen actuator setup?
  - can the state be driven through the required part of the state space?

## Observability
- **Observability** asks whether the available measurements are enough to infer the internal state.
- Practical meaning:
  - can an observer exist for the chosen sensor setup?
  - can the controller know enough about the state to stabilise the system?

## Formal Statements
### Controllability
- A system is **completely state controllable** if for initial state $x(0)$ and final state $x(NT)$ there exists an input sequence $u(k)$ for some finite $N$ that transfers the state as required.
- The system is controllable if the controllability matrix is full rank:
$$
\mathcal{C}_{GH} = \begin{bmatrix} H & GH & G^2H & \cdots & G^{n-1}H \end{bmatrix}
$$

### Observability
- A system is **observable** if the initial state $x(0)$ can be uniquely determined from the outputs and input sequence over a finite interval.
- The system is observable if the observability matrix is full rank:
$$
\mathcal{O}_{GC} = \begin{bmatrix}
C^T & (CG)^T & (CG^2)^T & \cdots & (CG^{n-1})^T
\end{bmatrix}^T
$$

## Practical Impact
| Property | Practical Question | Design Consequence |
|---|---|---|
| **Controllability** | Do the actuators give enough authority? | Enables state-feedback pole placement |
| **Observability** | Do the sensors reveal enough information? | Enables observer/state estimation design |

## Notes
- The workshop frames these as design-enabling tests rather than just definitions.
- In the slides, observability is described in terms of recovering the initial state from output and input data.
- One slide appears to contain a typo stating the system is controllable if $\mathcal{O}_{GC}$ is full rank; context shows this should read **observable**.

## Links
- [[Direct Discrete Design Workshop View]]
- [[Aircraft Controllability and Observability Check]]
- [[Aircraft State Feedback Design]]

## Visual Placeholders
![[Controllability and Observability Summary.png|400]]
