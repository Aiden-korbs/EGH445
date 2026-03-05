> [!info] Extracting Specific Transfer Functions
> 
> For a system with multiple inputs $u = \begin{bmatrix} u_1 \\ u_2 \end{bmatrix}$ and outputs $y = \begin{bmatrix} y_1 \\ y_2 \end{bmatrix}$, the transfer function matrix $G(s) = C(sI - A)^{-1}B + D$ will be a $2 \times 2$ matrix.
> 
> To find $H_1(s) = \frac{y_1(s)}{u_1(s)}$, you look at row 1, column 1 of $G(s)$.
> 
> To find $H_2(s) = \frac{y_2(s)}{u_1(s)}$, you look at row 2, column 1 of $G(s)$.

### 1. The Problem Statement

Given the following state-space representation of an electromechanical system:

$$\begin{bmatrix} \dot{x}_1 \\ \dot{x}_2 \end{bmatrix} = \begin{bmatrix} -2 & -1 \\ 3 & -4 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} + \begin{bmatrix} 1 & 0 \\ 0 & -2 \end{bmatrix} \begin{bmatrix} u_1 \\ u_2 \end{bmatrix}$$

$$\begin{bmatrix} y_1 \\ y_2 \end{bmatrix} = \begin{bmatrix} 0 & 2 \\ 1 & 0 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix}$$

a) Obtain the transfer functions $H_1(s) = \frac{y_1(s)}{u_1(s)}$ and $H_2(s) = \frac{y_2(s)}{u_1(s)}$.

### 2. Identify the Matrices

$$A = \begin{bmatrix} -2 & -1 \\ 3 & -4 \end{bmatrix}, \quad B = \begin{bmatrix} 1 & 0 \\ 0 & -2 \end{bmatrix}, \quad C = \begin{bmatrix} 0 & 2 \\ 1 & 0 \end{bmatrix}, \quad D = \begin{bmatrix} 0 & 0 \\ 0 & 0 \end{bmatrix}$$

### 3. Construct $(sI - A)$

$$sI - A = \begin{bmatrix} s & 0 \\ 0 & s \end{bmatrix} - \begin{bmatrix} -2 & -1 \\ 3 & -4 \end{bmatrix} = \begin{bmatrix} s+2 & 1 \\ -3 & s+4 \end{bmatrix}$$

### 4. Find the Inverse: $(sI - A)^{-1}$

**a) Calculate the determinant:**

$$\det(sI - A) = (s+2)(s+4) - (1)(-3)$$

$$\det(sI - A) = (s^2 + 4s + 2s + 8) + 3 = s^2 + 6s + 11$$

**b) Find the adjugate matrix:**

$$\text{adj}(sI - A) = \begin{bmatrix} s+4 & -1 \\ 3 & s+2 \end{bmatrix}$$

**c) Combine for the inverse:**

$$(sI - A)^{-1} = \frac{1}{s^2 + 6s + 11} \begin{bmatrix} s+4 & -1 \\ 3 & s+2 \end{bmatrix}$$

### 5. Calculate $G(s) = C(sI - A)^{-1}B$

**a) Multiply inverse by $B$:**

$$\begin{bmatrix} s+4 & -1 \\ 3 & s+2 \end{bmatrix} \begin{bmatrix} 1 & 0 \\ 0 & -2 \end{bmatrix} = \begin{bmatrix} (s+4)(1) + (-1)(0) & (s+4)(0) + (-1)(-2) \\ (3)(1) + (s+2)(0) & (3)(0) + (s+2)(-2) \end{bmatrix}$$

$$= \begin{bmatrix} s+4 & 2 \\ 3 & -2s-4 \end{bmatrix}$$

**b) Multiply the result by $C$:**

$$\begin{bmatrix} 0 & 2 \\ 1 & 0 \end{bmatrix} \begin{bmatrix} s+4 & 2 \\ 3 & -2s-4 \end{bmatrix} = \begin{bmatrix} (0)(s+4) + (2)(3) & (0)(2) + (2)(-2s-4) \\ (1)(s+4) + (0)(3) & (1)(2) + (0)(-2s-4) \end{bmatrix}$$

$$= \begin{bmatrix} 6 & -4s-8 \\ s+4 & 2 \end{bmatrix}$$

**c) Combine with the determinant to get the full Transfer Function Matrix $G(s)$:**

$$G(s) = \frac{1}{s^2 + 6s + 11} \begin{bmatrix} 6 & -4s-8 \\ s+4 & 2 \end{bmatrix} = \begin{bmatrix} \frac{6}{s^2 + 6s + 11} & \frac{-4s-8}{s^2 + 6s + 11} \\ \\ \frac{s+4}{s^2 + 6s + 11} & \frac{2}{s^2 + 6s + 11} \end{bmatrix}$$

### 6. Extract the Required Transfer Functions

The problem asks for specific relationships driven by the first input, $u_1$.

- $H_1(s) = \frac{y_1(s)}{u_1(s)}$ corresponds to **Row 1, Column 1** of $G(s)$.
    
- $H_2(s) = \frac{y_2(s)}{u_1(s)}$ corresponds to **Row 2, Column 1** of $G(s)$.
    

**Final Answers:**

$$H_1(s) = \frac{6}{s^2 + 6s + 11}$$

$$H_2(s) = \frac{s+4}{s^2 + 6s + 11}$$