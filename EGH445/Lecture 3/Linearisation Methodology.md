← Back to [[Nonlinear Systems and Linearisation]]
## Objective
* Many real dynamical systems are nonlinear but operate near equilibrium points.
* Linearisation creates a linear system approximation to model small deviations from an equilibrium point, enabling the use of linear control design tools.

## Methodological Steps
1. **Find Equilibrium Points**: Solve $0 = f(\overline{x}, \overline{u})$.Choose a specific steady-state point and input if multiple exist.
2. **Define Incremental System Model**: Create new variables representing the small deviation from equilibrium: $\delta x := x - \overline{x}$ and $\delta u := u - \overline{u}$. 
3. **Approximate the Model**: Use Taylor's formula around the set point $\overline{x}$. Because the system is at equilibrium, $f(\overline{x}) = 0$, and higher-order terms $E(\overline{x}, \delta x)$ are ignored, leaving the linear approximation [.
4. **Determine Jacobians**: Extract the state matrix ($A$) and input matrix ($B$) using partial derivatives (see [[Jacobian Matrices in Linearisation]]).
5. **(Optional) Output Model**: Apply the same incremental approach to the output equation to find matrices $C$ and $D$.