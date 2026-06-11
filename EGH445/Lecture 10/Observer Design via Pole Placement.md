# Observer Design via Pole Placement

← Back to [[State Estimation: Observers and Output Feedback]]

## Goal

Choose the observer gain $L$ so that the error dynamics $e(kT+T) = (G - LC)e(kT)$ are stable and converge quickly.

## Theorem

If the pair $(G, C)$ is completely observable, then we can **arbitrarily assign** the eigenvalues of $(G - LC)$ by choosing the appropriate observer gain $L$.

## Design Steps

1. **Check Observability**: Verify $\text{rank}(\mathcal{O}) = n$

2. **Choose Desired Observer Poles**: Select stable pole locations $z_1, z_2, \ldots, z_n$ within the unit circle, $|z_i| < 1$.
   - These poles dictate the speed of convergence of $e(kT)$
   - Typically chosen **5–10 times faster** (closer to the origin) than controller poles

3. **Form Desired Characteristic Polynomial**:

$$(z - z_1)(z - z_2)\cdots(z - z_n)$$

4. **Determine Observer Gain $L$**: Find $L$ such that $\det(zI - (G - LC))$ matches the desired polynomial.

## Duality with Controller Design

| State-Feedback Control | Observer Design |
|------------------------|-----------------|
| Find $K$ to place eigenvalues of $(G - HK)$ | Find $L$ to place eigenvalues of $(G - LC)$ |
| Requires $(G, H)$ controllable | Requires $(G, C)$ observable |

### Duality Property

$$\text{eig}(G - LC) = \text{eig}((G - LC)^\top) = \text{eig}(G^\top - C^\top L^\top)$$

Designing $L$ for $(G - LC)$ is dual to designing $K_{\text{obs}}$ for $(G^\top - C^\top K_{\text{obs}})$.

## Implementation

| Control Design | Observer Design |
|---------------|-----------------|
| `K = place(G, H, p)` | `L = place(G', C', p)'` |
| MATLAB | MATLAB |
| `control.place(G, H, p)` | `L = control.place(G.T, C.T, p).T` |
| Python | Python |

## Example

System: Vehicle model with $C = \begin{bmatrix} 1 & 0 \end{bmatrix}$

- **Controller poles**: $\{0.8, 0.7\}$
- **Observer poles** (faster): $\{0.2, 0.3\}$

$$K = \text{place}(G, H, [0.8, 0.7]) \rightarrow K = \begin{bmatrix} 6.1512 & 4.3159 \end{bmatrix}$$

$$L = \text{place}(G', C', [0.2, 0.3])' \rightarrow L = \begin{bmatrix} 1.4418 \\ 4.7007 \end{bmatrix}$$
