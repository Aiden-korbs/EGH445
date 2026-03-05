> [!info] The Core Formula
> 
> To convert a state-space model ($\dot{x} = Ax + Bu$, $y = Cx + Du$) to a transfer function $G(s)$, we use the following equation:
> 
> $$G(s) = C(sI - A)^{-1}B + D$$

### 1. The Problem Statement

Given the following state-space representation, find the transfer function matrix $G(s)$:

$$\begin{bmatrix} \dot{x}_1 \\ \dot{x}_2 \end{bmatrix} = \begin{bmatrix} -2 & -1 \\ 2 & -1 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} + \begin{bmatrix} 1 \\ 2 \end{bmatrix} u$$

$$y = \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix}$$

### 2. Identify the Matrices

From the standard form, we can extract our $A$, $B$, $C$, and $D$ matrices. (Note: Since there is no $+ Du$ in the output equation, $D$ is a zero matrix).

$$A = \begin{bmatrix} -2 & -1 \\ 2 & -1 \end{bmatrix}, \quad B = \begin{bmatrix} 1 \\ 2 \end{bmatrix}, \quad C = \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix}, \quad D = \begin{bmatrix} 0 \\ 0 \end{bmatrix}$$

### 3. Construct $(sI - A)$

First, multiply the complex frequency $s$ by the $2 \times 2$ identity matrix $I$, then subtract matrix $A$.

$$sI = \begin{bmatrix} s & 0 \\ 0 & s \end{bmatrix}$$

$$sI - A = \begin{bmatrix} s & 0 \\ 0 & s \end{bmatrix} - \begin{bmatrix} -2 & -1 \\ 2 & -1 \end{bmatrix} = \begin{bmatrix} s+2 & 1 \\ -2 & s+1 \end{bmatrix}$$

### 4. Find the Inverse: $(sI - A)^{-1}$

To find the inverse of a $2 \times 2$ matrix, use the formula $\frac{1}{\det} \text{adj}(M)$.

**a) Calculate the determinant:**

$$\det(sI - A) = (s+2)(s+1) - (1)(-2)$$

$$\det(sI - A) = (s^2 + s + 2s + 2) + 2 = s^2 + 3s + 4$$

**b) Find the adjugate matrix:**

Swap the elements on the main diagonal, and multiply the off-diagonal elements by -1.

$$\text{adj}(sI - A) = \begin{bmatrix} s+1 & -1 \\ 2 & s+2 \end{bmatrix}$$

**c) Combine for the inverse:**

$$(sI - A)^{-1} = \frac{1}{s^2 + 3s + 4} \begin{bmatrix} s+1 & -1 \\ 2 & s+2 \end{bmatrix}$$

### 5. Multiply by $B$ and $C$

Now, plug the inverse back into the core formula: $G(s) = C(sI - A)^{-1}B$.

First, let's calculate $(sI - A)^{-1}B$:

$$\begin{bmatrix} s+1 & -1 \\ 2 & s+2 \end{bmatrix} \begin{bmatrix} 1 \\ 2 \end{bmatrix} = \begin{bmatrix} (s+1)(1) + (-1)(2) \\ (2)(1) + (s+2)(2) \end{bmatrix}$$

$$= \begin{bmatrix} s + 1 - 2 \\ 2 + 2s + 4 \end{bmatrix} = \begin{bmatrix} s - 1 \\ 2s + 6 \end{bmatrix}$$

Next, multiply by $C$. Since our $C$ matrix is the identity matrix $\begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix}$, multiplying it by our current vector doesn't change anything.

Finally, distribute the determinant denominator back into the matrix.

### Final Answer

The transfer function matrix $G(s)$ relates the input $u$ to the two outputs $y_1$ and $y_2$:

$$G(s) = \begin{bmatrix} \frac{s - 1}{s^2 + 3s + 4} \\ \\ \frac{2s + 6}{s^2 + 3s + 4} \end{bmatrix}$$