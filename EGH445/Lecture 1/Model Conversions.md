## 1. ODE to Transfer Function
Transform the $n$-th order ODE using Laplace:  
$$y^{(n)} + a_{n-1}y^{(n-1)} + \dots + a_0y = b_0u$$
**Result**:$$H(s) = \frac{Y(s)}{U(s)} = \frac{b_0}{s^n + a_{n-1}s^{n-1} + \dots + a_0}$$  

## 2. ODE to State-Space (Phase Variables)
For an $n$-th order ODE, define $n$ states as derivatives:  
*$x_1 = y, x_2 = \dot{y}, \dots, x_n = y^{(n-1)}$  
**Matrix Structure**:$$A = \begin{bmatrix} 0 & 1 & 0 & \dots \\ 0 & 0 & 1 & \dots \\ \vdots & \vdots & \vdots & \ddots \\ -a_0 & -a_1 & -a_2 & \dots \end{bmatrix}, B = \begin{bmatrix} 0 \\ 0 \\ \vdots \\ b_0 \end{bmatrix}, C = \begin{bmatrix} 1 & 0 & \dots & 0 \end{bmatrix}$$  

## 3. State-Space to Transfer Function 
Using Laplace transform properties on $\dot{x} = Ax + Bu$:$$sX(s) - AX(s) = BU(s) \implies X(s) = (sI - A)^{-1}BU(s)$$  
**Formula**:$$H(s) = C(sI - A)^{-1}B + D$$  
**Scalar Calculation (SISO)**:$$H(s) = \frac{C \text{adj}(sI - A)B + \det(sI - A)D}{\det(sI - A)}$$  

> [!TIP]
>The poles of $H(s)$ are the **eigenvalues** of the matrix $A$.  