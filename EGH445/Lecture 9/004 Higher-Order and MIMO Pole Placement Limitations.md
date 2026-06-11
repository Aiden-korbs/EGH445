# Higher-Order and MIMO Pole Placement Limitations

## Higher-Order Systems

For a higher-order system ($n > 3$):

$$x(kT + T) = G x(kT) + H u(kT)$$
$$y(kT) = C x(kT) + D u(kT)$$

where $x(kT) \in \mathbb{R}^n$, $u(kT) \in \mathbb{R}$, $y(kT) \in \mathbb{R}$, $n > 3$.

**Key challenge:** The link between pole locations and desired time-domain response becomes increasingly ambiguous. Arbitrary pole choices can lead to poor performance or excessive control effort.

**Core question:** How do you choose the best pole locations for a 5th, 10th, or higher-order system?

## MIMO Systems

Consider a simple MIMO system with two states and two inputs:

$$x(kT + T) = \begin{bmatrix} 1 & 0.1 \\ 0 & 0.8 \end{bmatrix} x(kT) + \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix} u(kT)$$

We want to place the poles at $z = 0.4$ and $z = 0.6$ using:

$$u(kT) = -K x(kT), \quad K = \begin{bmatrix} k_1 & k_2 \\ k_3 & k_4 \end{bmatrix}$$

The closed-loop characteristic polynomial is:

$$\det(zI - (G - HK)) = \det\begin{bmatrix} z - 1 + k_1 & k_2 - 0.1 \\ k_3 & z - 0.8 + k_4 \end{bmatrix}$$

$$= z^2 + (k_1 + k_4 - 1.8)z + (0.1k_3 - k_4 - 0.8k_1 + k_1k_4 - k_2k_3 + 0.8)$$

The desired characteristic polynomial for poles at $0.4$ and $0.6$ is:

$$(z - 0.4)(z - 0.6) = z^2 - 1z + 0.24$$

Equate coefficients:

$$\begin{cases} k_1 + k_4 - 1.8 = -1 \\ 0.1k_3 - k_4 - 0.8k_1 + k_1k_4 - k_2k_3 + 0.8 = 0.24 \end{cases}$$

**Result:** 2 equations, 4 unknowns — two degrees of freedom remain.

## Eigenvector Sensitivity

Different choices of $K$ that yield the same eigenvalues can produce different eigenvectors, which directly affect the system response.

For example, setting $k_2 = k_3 = 0$:

$$K_1 = \begin{bmatrix} 0.6 & 0 \\ 0 & 0.2 \end{bmatrix}, \quad K_2 = \begin{bmatrix} 0.4 & 0 \\ 0 & 0.4 \end{bmatrix}$$

Both yield the same eigenvalues ($0.4$ and $0.6$), but simulations show different closed-loop responses.

## MIMO Summary

For MIMO systems ($x(kT) \in \mathbb{R}^n$, $u(kT) \in \mathbb{R}^m$, $y(kT) \in \mathbb{R}^p$, $n, m, p > 1$):

- Pole placement is significantly more complex
- Specifying only eigenvalues leaves degrees of freedom in eigenvectors
- The design process is non-unique and less intuitive
- Handling interactions between inputs and outputs requires systematic approaches

## Key Takeaways

- Higher-order systems: no clear guidance on pole selection; arbitrary choices risk poor performance
- MIMO systems: eigenvalue placement alone is insufficient; eigenvectors matter too
- Both cases call for optimality-based design methods like LQR/MPC

## Related

- [[003 Pole Placement- When It Works and When It Fails]]
- [[005 Pole Placement Control Effort Trade-offs]]
- [[007 Discrete Linear Quadratic Regulator DLQR]]
