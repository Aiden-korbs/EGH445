# Controllability

## Core Idea
- **Controllability** asks whether a system can be forced to a desired state using an input sequence.
- In discrete time, we work with **sampled sequences** instead of continuous signals.

## Definitions
### Null controllability
- A system is **null controllable** if there exists an input sequence that transfers an initial state $x(0)$ to the zero state in finite time.

### Reachability
- A state is **reachable** if, starting from the zero state, there exists an input sequence that reaches a desired final state $x(N)$ in finite time.

### Complete state controllability
- A system is **completely state controllable** if, for any initial state $x(0)$ and any desired final state $x(N)$, there exists an input sequence that transfers one to the other in finite time.

### Complete output controllability
- A system is **completely output controllable** if any final output $y(N)$ can be reached from any initial state using an unconstrained input sequence.

## LTI View
- For **linear time-invariant** systems, reachability and controllability are treated as equivalent ideas in this lecture.
- If a state is **uncontrollable**, no input can directly manipulate that mode.

## State-Space Context
For the discrete model
$$
x(kT+T)=Gx(kT)+Hu(kT)
$$
$$
y(kT)=Cx(kT)+Du(kT)
$$
the controllability test uses the pair $(G,H)$.

## Controllability Matrix
The controllability matrix is
$$
\mathcal{C}_{GH}=\begin{bmatrix} H & GH & G^2H & \cdots & G^{n-1}H \end{bmatrix}
$$

## Test
- A system of order $n$ is completely controllable iff
$$
\operatorname{rank}(\mathcal{C}_{GH})=n
$$

## Practical Notes
- For square matrices, checking
$$
\det(\mathcal{C}_{GH})\neq 0
$$
also shows full rank.
- Affine or similarity changes of state variables do **not** change the rank result.

## Why It Matters for Design
- [[Discrete State Feedback]] and [[Pole Placement Gain Methods]] assume the system is controllable.
- Without controllability, not all closed-loop poles can be moved to chosen locations.

## Links
- [[Observability]]
- [[State Feedback Design Procedure]]
- [[Discrete-Time Controllability and Observability Nuances]]

## Visual Placeholders
![[Controllability Test Diagram.png|400]]
