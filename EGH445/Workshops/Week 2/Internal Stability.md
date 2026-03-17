← Back to [[Week 2 Workshop - System Response and Stability]]

# Internal Stability

## Definition
A (SISO/MIMO) homogeneous LTI system is **internally stable** if for **every initial condition**, all states **decay to zero**:

$$\|x\| \to 0 \quad \text{as} \quad t \to \infty$$

## Stability Condition
The linear homogeneous system $\dot{x} = Ax$ is internally stable **if and only if** the **real parts of all eigenvalues of $A$ are negative**:

$$\text{Re}(\lambda_i) < 0 \quad \forall \; i$$

## Connection to the State Transition Matrix
Setting $u(t) = 0$ for $t > t_0$ in the full solution:

$$x = e^{At} x_0 + \int_0^t e^{A(t-\tau)} B u(\tau) \, d\tau$$

The stability depends entirely on $e^{At}$, and via the [[State Transition Matrix]] eigendecomposition:

$$e^{At} = T \begin{bmatrix} e^{\lambda_1 t} & \cdots & 0 \\ \vdots & \ddots & \vdots \\ 0 & \cdots & e^{\lambda_n t} \end{bmatrix} T^{-1}$$

- If all $\text{Re}(\lambda_i) < 0$, then each $e^{\lambda_i t} \to 0$ as $t \to \infty$ → system is stable.
- The same system, even if coordinate-transformed, has the same eigenvalues.

## Relationship to BIBO Stability
- Internal stability of $\dot{x} = Ax$ **implies** [[BIBO Stability]] of the system with inputs and outputs.
- Internal stability is the **stronger** condition.

> **Pole-zero cancellation warning:** A pole cancelled in the transfer function still exists physically. Internal states tied to that pole may be unstable even if $H(s)$ appears BIBO stable.

## Related Notes
- [[BIBO Stability]]
- [[Lyapunov Stability]]
- [[State Transition Matrix]]
