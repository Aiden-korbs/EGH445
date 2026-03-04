## Fundamental Definitions
Modern control relies on the **Input-State-Output Model**.

***State Vector ($x$)**: A group of variables representing the system dynamics completely.
	*$x(t) \in \mathbb{R}^n$
***Input Vector ($u$)**: $u(t) \in \mathbb{R}^m$
***Output Vector ($y$)**: $y(t) \in \mathbb{R}^p$

## Linear Time-Invariant (LTI) Equations
The standard form for LTI systems is:
$$\dot{x} = Ax + Bu$$
$$y = Cx + Du$$

### Matrix Dimensions
***State Matrix ($A$)**: $n \times n$
***Input Matrix ($B$)**: $n \times m$
***Output Matrix ($C$)**: $p \times n$
***Direct Feedthrough Matrix ($D$)**: $p \times m$

### Properties
*The current state $x(t_0)$ summarises all past information.
* Future outputs are determined by the current state and future inputs.
* Other variables of interest are obtained via static relations (Output Equation).