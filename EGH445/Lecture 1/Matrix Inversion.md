## Overview 
Calculating the inverse of a matrix is a critical step in converting [[State-Space Modelling|state-space models]] to [[Model Conversions|transfer functions]] . For the purposes of EGH445, calculations for $A \in \mathbb{R}^{2 \times 2}$ are expected to be done by hand, while larger matrices utilise software .

## General Formula 
The inverse of a matrix can be expressed using the **cofactor/adjoint matrix** and the **determinant**: $$(sI - A)^{-1} = \frac{\text{adj}(sI - A)}{\det(sI - A)}$$ ## The $2 \times 2$ Case For a matrix $A = \begin{bmatrix} a_{11} & a_{12} \\ a_{21} & a_{22} \end{bmatrix}$ :

| Component | Formula |
| :--- | :--- |
| **Determinant** | $\det(A) = a_{11}a_{22} - a_{12}a_{21}$ |
| **Adjoint** | $\text{adj}(A) = \begin{bmatrix} a_{22} & -a_{12} \\ -a_{21} & a_{11} \end{bmatrix}$ |

---

## Applied Scenario: Mass-Spring-Damper Inverse


### Scenario 
Calculate $(sI - A)^{-1}$ for a mass-spring-damper system to derive its transfer function .

### Given
* State Matrix $A = \begin{bmatrix} 0 & 1/m \\ -k & -b/m \end{bmatrix}$ * Identity Matrix $I = \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix}$ ### Steps
1. **Form the $(sI - A)$ matrix**: $$(sI - A) = \begin{bmatrix} s & 0 \\ 0 & s \end{bmatrix} - \begin{bmatrix} 0 & 1/m \\ -k & -b/m \end{bmatrix} = \begin{bmatrix} s & -1/m \\ k & s + b/m \end{bmatrix}$$ 2. **Calculate the Determinant**: $$\det(sI - A) = (s)(s + b/m) - (-1/m)(k) = s^2 + \frac{b}{m}s + \frac{k}{m}$$ 3. **Calculate the Adjoint**: $$\text{adj}(sI - A) = \begin{bmatrix} s + b/m & 1/m \\ -k & s \end{bmatrix}$$ 4. **Form the Inverse**: $$(sI - A)^{-1} = \frac{1}{s^2 + \frac{b}{m}s + \frac{k}{m}} \begin{bmatrix} s + b/m & 1/m \\ -k & s \end{bmatrix}$$
### Final Notes
* The denominator is the **characteristic polynomial** of the system .
* For systems larger than $2 \times 2$, use **MATLAB** commands like `inv(A)` or symbolic math tools .