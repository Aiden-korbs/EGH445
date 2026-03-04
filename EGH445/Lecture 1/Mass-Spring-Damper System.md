## Scenario 
A mechanical system consisting of a mass ($m$), a spring with constant ($k$), and a damper with coefficient ($b$) subject to an external force $u(t)$.

## Given
*Equation of Motion (ODE): $m\ddot{y} + b\dot{y} + ky = u(t)$
*$y$: Position
*$\dot{y}$: Velocity

## Steps
1. **Define States**:
	*$x_1 = y$ (position)
	*$x_2 = \dot{y}$ (velocity)
2. **Derive State Derivatives**:
	*$\dot{x}_1 = \dot{y} = x_2$
	*$\dot{x}_2 = \ddot{y} = -\frac{k}{m}x_1 - \frac{b}{m}x_2 + \frac{1}{m}u$
3. **Formulate Matrices**:
	*$A = \begin{bmatrix} 0 & 1 \\ -\frac{k}{m} & -\frac{b}{m} \end{bmatrix}$
	*$B = \begin{bmatrix} 0 \\ \frac{1}{m} \end{bmatrix}$
	*$C = \begin{bmatrix} 1 & 0 \end{bmatrix}$
	*$D = [0]$

## Final Notes
The resulting state-space model represents a 2nd-order system as two coupled 1st-order differential equations.

![[Mass Spring Damper Diagram.png|400]]