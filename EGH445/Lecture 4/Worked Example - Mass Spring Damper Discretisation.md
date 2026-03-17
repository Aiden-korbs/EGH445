← Back to [[Discrete-time Control System Modelling]]

# Worked Example — Mass-Spring-Damper Discretisation

## Scenario
Find the discrete-time state-space model directly from the continuous-time state-space model using sampling time $T = 1\,\text{s}$.

## Given

**Continuous-time state space model (mass-spring-damper):**

$$\dot{x}(t) = \begin{bmatrix} 0 & 1 \\ -1 & -2 \end{bmatrix} x(t) + \begin{bmatrix} 0 \\ 1 \end{bmatrix} u(t), \qquad y(t) = \begin{bmatrix} 0 & 1 \end{bmatrix} x(t)$$

**System parameters:** $b = 2$ (damper), $m = 1$ (mass), $c = 1$ (spring)

**Sampling time:** $T = 1\,\text{s}$

**Objective:** Find $G$ and $H$ (note: $C$ and $D$ are unchanged in the discrete model).

---

## Step 1 — Check Invertibility of $A$

$$|A| = (0 \times -2) - (-1 \times 1) = 1 \neq 0$$

$A$ is **invertible** → we can use $H = A^{-1}(G - I)B$ once $G$ is found.

---

## Step 2 — Find $G$ Using Three Methods

### Method 1 — Power Series (2nd Order Approximation)

$$G \approx \hat{G} = I + AT + \frac{1}{2!}A^2T^2$$

$$= \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix} + \begin{bmatrix} 0 & 1 \\ -1 & -2 \end{bmatrix} + \frac{1}{2}\begin{bmatrix} 0 & 1 \\ -1 & -2 \end{bmatrix}^2$$

$$\hat{G} = \begin{bmatrix} 1 & 1 \\ -1 & -1 \end{bmatrix} + \frac{1}{2}\begin{bmatrix} -1 & -2 \\ 2 & 3 \end{bmatrix} = \begin{bmatrix} 0.5 & 0 \\ 0 & 0.5 \end{bmatrix}$$

### Method 2 — Laplace Transform (Exact)

$$G = \mathcal{L}^{-1}\{(sI - A)^{-1}\}\big|_{t=T}$$

$$sI - A = \begin{bmatrix} s & -1 \\ 1 & s+2 \end{bmatrix}, \qquad (sI-A)^{-1} = \frac{1}{(s+1)^2}\begin{bmatrix} s+2 & 1 \\ -1 & s \end{bmatrix}$$

After partial fraction expansion (PFE):

$$G = \mathcal{L}^{-1}\left\{ \begin{bmatrix} \frac{s}{(s+1)^2} + \frac{2}{(s+1)^2} & \frac{1}{(s+1)^2} \\ \frac{-1}{(s+1)^2} & \frac{s}{(s+1)^2} \end{bmatrix} \right\}$$

Using Laplace pairs $\frac{1}{(s+a)^2} \to te^{-at}$ and $\frac{s}{(s+a)^2} \to (1-at)e^{-at}$:

$$G = \begin{bmatrix} (1-T)e^{-T} + 2Te^{-T} & Te^{-T} \\ -Te^{-T} & (1-T)e^{-T} \end{bmatrix}\bigg|_{T=1}$$

$$\boxed{G = \begin{bmatrix} 0.7358 & 0.3679 \\ -0.3679 & 0 \end{bmatrix}}$$

### Method 3 — Similarity Transform

$A$ has **repeated eigenvalues** at $\lambda = -1$ (eigenvalue of multiplicity 2).

The similarity transform method **cannot** be used directly — Jordan block form would be required, which is out of scope for EGH445. MATLAB's `eig(A)` confirms: $\det(P) \approx 0$.

---

## Step 3 — Find $H$

Using $H = A^{-1}(G - I)B$ with the exact $G$ from Method 2:

$$A^{-1} = \frac{1}{\det(A)}\begin{bmatrix} -2 & -1 \\ 1 & 0 \end{bmatrix} = \begin{bmatrix} -2 & -1 \\ 1 & 0 \end{bmatrix}$$

$$G - I = \begin{bmatrix} 0.7358 - 1 & 0.3679 \\ -0.3679 & 0 - 1 \end{bmatrix} = \begin{bmatrix} -0.2642 & 0.3679 \\ -0.3679 & -1 \end{bmatrix}$$

$$H = \begin{bmatrix} -2 & -1 \\ 1 & 0 \end{bmatrix} \begin{bmatrix} 0.3679 \\ -1 \end{bmatrix} = \begin{bmatrix} 0.2642 \\ 0.3679 \end{bmatrix}$$

$$\boxed{H = \begin{bmatrix} 0.2642 \\ 0.3679 \end{bmatrix}}$$

---

## Final Discrete-Time State Space Model (Method 2 / Exact)

$$x(kT+T) = \begin{bmatrix} 0.7358 & 0.3679 \\ -0.3679 & 0 \end{bmatrix} x(kT) + \begin{bmatrix} 0.2642 \\ 0.3679 \end{bmatrix} u(kT)$$

$$y(kT) = \begin{bmatrix} 0 & 1 \end{bmatrix} x(kT)$$

---

## Analysis and Insights

| Model | Quality |
| :--- | :--- |
| Method 1 (2nd order approx, $T=1$) | **Poor** — $y(kT)$ does not follow $y(t)$; ZOH effects invisible |
| Method 2 (Laplace, $T=1$) | **Good** — $y(kT)$ closely follows $y(t)$; ZOH staircase visible |
| Method 2 (Laplace, $T=0.1$) | **Better** — even closer to continuous; ZOH lag less visible |

**Effect of sampling time $T$:**
- As $T$ decreases (higher sampling frequency), the discrete output $y(kT)$ better resembles $y(t)$.
- The ZOH introduces less lag when $T$ is small.
- The exact model (Method 2/MATLAB) is always preferred over approximations.

---

## MATLAB Code

```matlab
% System Parameters
T = 1;
A = [0 1; -1 -2]; B = [0; 1]; C = [0 1]; D = 0;

% Discrete State Transition Matrix - Exact
G = expm(A .* T)

% Discrete Input Matrix - Exact (A invertible)
H = inv(A) * (G - eye(size(G))) * B

% Build State Space Models
CSS = ss(A, B, C, D);           % Continuous
[G, H] = c2d(A, B, T);         % Discrete conversion
DSS = ss(G, H, C, D, T);       % Discrete SS

% Transfer Functions
[num, den] = ss2tf(A, B, C, D, 1);
Gs = tf(num, den);
[num, den] = ss2tf(G, H, C, D, 1);
Gz = tf(num, den, T);

% Impulse Response Comparison
figure(1); hold on
t = 0:T:10;
impulseplot(Gs, t(end), 'k-')
[yi, ti, xi] = impulse(Gz, t);
stairs(ti, yi, 'r.-')
```

## Related Notes
- [[Discrete State Space Models - Overview]]
- [[Finding the G Matrix]]
- [[Finding the H Matrix]]
- [[Difference Equations]]
- [[Zero Order Hold and Data Hold]]
- [[Sampling Time and Frequency Selection]]
