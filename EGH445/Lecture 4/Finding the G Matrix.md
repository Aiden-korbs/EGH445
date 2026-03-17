← Back to [[Discrete-time Control System Modelling]]

# Finding the G Matrix

## Definition

$$\boxed{G = e^{AT}}$$

$G$ is the **discrete state transition matrix** — the matrix exponential of $A$ evaluated at the sampling period $T$.

---

## Method 1 — Power Series (Approximate, $n$th Order)

$$G = e^{AT} = \sum_{k=0}^{\infty} \frac{1}{k!} A^k T^k = I + AT + \frac{1}{2!}A^2T^2 + \frac{1}{3!}A^3T^3 + \cdots$$

Truncate to desired order:

| Order | Expression |
| :--- | :--- |
| **1st Order** | $G \approx I + AT$ |
| **2nd Order** | $G \approx I + AT + \frac{1}{2}A^2T^2$ |
| **$\infty$ Order** | Full series (exact) |

> Low-order approximations are easy to compute by hand but can give poor representations depending on the dynamics and sampling time — analogous to using poor numerical integration.

---

## Method 2 — Laplace Transform (Exact)

Start from the homogeneous solution $\dot{x} = Ax \to x(t) = e^{At}x(0)$.

Take the Laplace transform:

$$\mathcal{L}\{\dot{x} = Ax\} \implies sX(s) - x(0) = AX(s)$$

$$X(s) = (sI - A)^{-1} x(0)$$

Taking the inverse Laplace transform and matching terms:

$$\boxed{e^{AT} = \mathcal{L}^{-1}\{(sI - A)^{-1}\}\big|_{t=T}}$$

> When taking the Laplace/inverse Laplace transform of a matrix, apply the transform **element-wise**. Use Laplace tables after rearranging each element into a recognisable form.

---

## Method 3 — Similarity Transform / Eigendecomposition (Exact, when $A$ is diagonalisable)

If $A$ has **unique eigenvalues**, it is diagonalisable:

$$P^{-1}AP = \Lambda = \begin{bmatrix} \lambda_1 & & \\ & \ddots & \\ & & \lambda_n \end{bmatrix}, \quad P = \begin{bmatrix} V_1 & \cdots & V_n \end{bmatrix}$$

where $V_i$ are eigenvectors and $\lambda_i$ are eigenvalues of $A$. Then:

$$\boxed{G = e^{AT} = Pe^{\Lambda T}P^{-1} = P \begin{bmatrix} e^{\lambda_1 T} & \cdots & 0 \\ \vdots & \ddots & \vdots \\ 0 & \cdots & e^{\lambda_n T} \end{bmatrix} P^{-1}}$$

The matrix exponential of a **diagonal matrix** is simply a diagonal matrix with $e^{\lambda_i T}$ on the diagonal.

> If $A$ has **repeated eigenvalues**, Jordan block matrices are required — this is **out of scope for EGH445**.

---

## Method Comparison

| Method | Type | When to Use | Limitations |
| :--- | :--- | :--- | :--- |
| Power Series | Approximate | Quick hand calculation | Requires small $T$; higher order = more work |
| Laplace Transform | Exact | General case | Requires PFE and inverse Laplace tables |
| Similarity Transform | Exact | $A$ has unique eigenvalues | Fails for repeated eigenvalues |
| MATLAB `expm(A*T)` | Exact | Always | Out of scope to understand method |

## MATLAB

```matlab
% Exact G using matrix exponential
G = expm(A * T);

% Exact G using eigendecomposition (check first)
[P, L] = eig(A);
if det(sym(P)) ~= 0
    Q = exp(L .* T) .* eye(size(A));
    G = P * Q * inv(P);
else
    disp('Repeated eigenvalues - similarity transform invalid')
end
```

## Related Notes
- [[Discrete State Space Models - Overview]]
- [[Finding the H Matrix]]
- [[Worked Example - Mass Spring Damper Discretisation]]
- [[State Transition Matrix]]
