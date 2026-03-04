## Concept Overview 
The transformation from **State-Space Equations** to **Transfer Functions** allows for the analysis of a system's input-output behaviour using $s$-domain algebraic methods.
## Mathematical Mapping 
The relationship is defined by the following mapping :

$$\text{State-Space} \begin{cases} \dot{x} = Ax + Bu \\ y = Cx + Du \end{cases} \longleftrightarrow H(s) = \frac{Y(s)}{U(s)} = C(sI - A)^{-1}B + D$$

---

## Derivation Steps 
By applying the **Laplace transform** to the time-domain equations, we directly obtain the $s$-domain representation :

### 1. Transform the Equations
* $s X(s) = A X(s) + B U(s)$ * $Y(s) = C X(s) + D U(s)$ 
 
### 2. Isolate the State Vector ($X(s)$) 
Rearrange the first equation to group terms containing $X(s)$ :
$$s X(s) - A X(s) = B U(s)$$
$$(sI - A) X(s) = B U(s)$$

> [!NOTE] Identity Matrix ($I$)
> The identity matrix $I$ is required to perform subtraction between the scalar $s$ and the matrix $A$ :
> $$I = \begin{bmatrix} 1 & 0 & \dots & 0 \\ \vdots & \ddots & & \vdots \\ 0 & 0 & \dots & 1 \end{bmatrix}$$

### 3. Account for Matrix Non-Commutativity 
Recalling that matrices, in general, **do not commute**, we multiply by the inverse from the left :
$$(sI - A)^{-1}(sI - A) X(s) = (sI - A)^{-1} B U(s)$$
$$X(s) = (sI - A)^{-1} B U(s)$$

### 4. Solve for the Transfer Function 
Substitute $X(s)$ back into the output equation :
$$Y(s) = [C (sI - A)^{-1} B + D] U(s)$$

---

## Applied Example: 
Mass-Spring-Damper System

### Scenario 
Calculating the transfer function for a 2nd-order mechanical system .

### Given
* Characteristic Polynomial: $s(s + b/m) + k/m = s^2 + \frac{b}{m}s + \frac{k}{m}$ * Output Matrix $C$: $[1 \quad 0]$ * Input Matrix $B$: $\begin{bmatrix} 0 \\ 1 \end{bmatrix}$ 
* ### Steps
1. **Matrix Multiplication**: Multiply the $C$ matrix by the adjoint matrix :
   $$\begin{bmatrix} 1 & 0 \end{bmatrix} \begin{bmatrix} s + b/m & 1/m \\ -k & s \end{bmatrix} = \begin{bmatrix} s + b/m & 1/m \end{bmatrix}$$
2. **Apply Input Matrix $B$**:
   $$\begin{bmatrix} s + b/m & 1/m \end{bmatrix} \begin{bmatrix} 0 \\ 1 \end{bmatrix} = 1/m$$
3. **Final Result**:
   $$H(s) = \frac{1/m}{s^2 + \frac{b}{m}s + \frac{k}{m}}$$
