← Back to [[Nonlinear Systems and Linearisation]]
## Matrix Definitions
When approximating an incremental model $\dot{\delta x} = A\delta x + B\delta u$, the matrices are derived by evaluating the Jacobians of the nonlinear functions $f$ at the chosen equilibrium point ($\overline{x}, \overline{u}$).

### State Matrix ($A$)
*Defined as the partial derivative of the system functions with respect to the state vector $x$.
 $$A = \left( \frac{\partial f}{\partial x} \right)^T \Bigg|_{x=\overline{x}, u=\overline{u}}$$
* Expands into an $n \times n$ matrix where element $A_{ij} = \frac{\partial f_i}{\partial x_j}$.

### Input Matrix ($B$)
* Defined as the partial derivative of the system functions with respect to the control input vector $u$.
$$B = \left( \frac{\partial f}{\partial u} \right)^T \Bigg|_{x=\overline{x}, u=\overline{u}}$$
* Expands into an $n \times m$ matrix where element $B_{ij} = \frac{\partial f_i}{\partial u_j}$

### Output Matrices ($C$ and $D$)
* Found similarly by taking the Jacobians of the output function $g(x, u)$.
* $C = \frac{\partial g}{\partial x}$ evaluated at $\overline{x}, \overline{u}$.
* $D = \frac{\partial g}{\partial u}$ evaluated at $\overline{x}, \overline{u}$.