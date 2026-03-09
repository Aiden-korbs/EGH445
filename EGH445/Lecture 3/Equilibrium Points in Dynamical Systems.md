← Back to [[Nonlinear Systems and Linearisation]]
## Core Concepts
* **Equilibrium Points** represent a stationary condition of a dynamical system.
* If a dynamical system starts with an initial condition at an equilibrium point $\overline{x}$, the state stays at that point forever ($x(t) = \overline{x}, \forall t \ge 0$).
* Mathematically, this implies the derivatives or rates of change of the system states are zero.

## Finding Equilibrium Points
### Autonomous Systems
* An autonomous system has no external forcing input ($u$).
* Model: $\dot{x} = f(x)$.
* To find equilibrium points, set the time derivative to zero and solve for $\overline{x}$: $0 = f(\overline{x})$ .

### Non-Autonomous Systems
* A non-autonomous system includes a control input ($u$).
* Model: $\dot{x} = f(x, u)$.
* Equilibrium points depend on the chosen steady-state input $\overline{u}$, which does not necessarily have to be zero.
* To find equilibrium points, solve the algebraic equations: $0 = f(\overline{x}, \overline{u})$.