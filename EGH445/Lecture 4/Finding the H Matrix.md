← Back to [[Discrete-time Control System Modelling]]

# Finding the H Matrix

## Definition

$$\boxed{H = \int_0^T e^{A\lambda}\,d\lambda\; B}$$

$H$ is the **discrete input matrix**, relating the held control input $u(kT)$ to the next state $x(kT+T)$.

---

## Method 1 — Using $G$ and $A^{-1}$ (When $A$ is Invertible)

If $A$ is **invertible** (non-singular, no eigenvalue at the origin), and $G$ is already known:

$$H = \int_0^T e^{A\lambda}\,d\lambda\; B = A^{-1}\int_0^T A e^{A\lambda}\,d\lambda\; B = A^{-1}\left[e^{A\lambda}\right]_0^T B$$

$$\boxed{H = A^{-1}(G - I)B = A^{-1}(e^{AT} - I)B}$$

> Check invertibility: $\det(A) \neq 0 \implies A$ is invertible.

**If $A$ is NOT invertible**, use the power series approximation:

$$H = \left(\sum_{k=0}^{\infty} \frac{1}{(k+1)!} A^k T^{k+1}\right) B = \left(IT + \frac{AT^2}{2} + \frac{1}{6}A^2T^3 + \cdots\right) B$$

> Mathematical identity used: $I = A^{-1}A$, $e^A = Ie^A$, and $\frac{d}{d\lambda}e^{A\lambda} = Ae^{A\lambda}$.

---

## Method 2 — Laplace Transform (Exact)

Recall from [[Finding the G Matrix]]:

$$e^{AT} = \mathcal{L}^{-1}\{(sI - A)^{-1}\}$$

It can be shown that:

$$\boxed{H = \mathcal{L}^{-1}\left\{(sI - A)^{-1} \frac{B}{s}\right\}\bigg|_{t=T}}$$

Use the Laplace transform of the integral of a function:

$$\mathcal{L}\int f(t)\,dt = \frac{F(s)}{s} + \frac{\int f(t)\,dt\big|_{t=0}}{s}$$

> Apply the inverse Laplace transform element-wise to the matrix. Use Laplace tables after rearranging each element.

**Useful Laplace Transforms for $H$:**

| $F(s)$ | $f(t)$ |
| :--- | :--- |
| $\dfrac{1}{(s+a)^2}$ | $te^{-at}$ |
| $\dfrac{s}{(s+a)^2}$ | $(1 - at)e^{-at}$ |
| $\dfrac{a^2}{s(s+a)^2}$ | $1 - e^{-at}(1 + at)$ |

---

## Method 3 — Similarity Transform (When $A$ is Diagonalisable)

If $A$ has unique eigenvalues (see [[Finding the G Matrix]] Method 3):

$$\boxed{H = \int_0^T e^{A\lambda}\,d\lambda\; B = \int_0^T Pe^{\Lambda\lambda}P^{-1}\,d\lambda\; B}$$

This is the exact integral form using the eigendecomposition of $A$.

---

## Method Comparison

| Method | Condition | Notes |
| :--- | :--- | :--- |
| $H = A^{-1}(G-I)B$ | $A$ invertible | Simple once $G$ is known |
| Power series | $A$ not invertible | Approximation; more terms = more accuracy |
| Laplace transform | General case | Exact; requires Laplace tables and PFE |
| Similarity transform | $A$ diagonalisable | Exact; fails for repeated eigenvalues |

## MATLAB

```matlab
A = [0 1; -1 -2];
B = [0; 1];
T = 1;

% Exact G
G = expm(A * T);

% Exact H (if A is invertible)
H = inv(A) * (G - eye(size(G))) * B;

% Or use MATLAB's built-in conversion
[G, H] = c2d(A, B, T);
```

## Related Notes
- [[Discrete State Space Models - Overview]]
- [[Finding the G Matrix]]
- [[Zero Order Hold and Data Hold]]
- [[Worked Example - Mass Spring Damper Discretisation]]
