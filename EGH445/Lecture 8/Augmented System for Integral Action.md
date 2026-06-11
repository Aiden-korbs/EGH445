# Augmented System for Integral Action

## Dynamic Extension
- Start with the plant:
$$
x(kT+T) = Gx(kT) + Hu(kT)
$$
$$
y(kT) = Cx(kT)
$$

- Add the integral state:
$$
q(kT+T) = q(kT) + y(kT) = q(kT) + Cx(kT)
$$

## Augmented State
Define
$$
z(kT) \equiv \begin{bmatrix} x(kT) \\ q(kT) \end{bmatrix}
$$

Then
$$
z(kT+T) =
\underbrace{\begin{bmatrix}
G & 0_{n\times p}\\
C & I_{p\times p}
\end{bmatrix}}_{G_z}
z(kT)
+
\underbrace{\begin{bmatrix}
H\\
0_{p\times m}
\end{bmatrix}}_{H_z}
u(kT)
$$

and
$$
y(kT) =
\underbrace{\begin{bmatrix}
C & 0_{p\times p}
\end{bmatrix}}_{C_z}
z(kT)
$$

## Augmented Control Law
$$
u(kT) = -K_z z(kT) = -\begin{bmatrix}K_x & K_I\end{bmatrix} z(kT)
$$
so
$$
u(kT) = -K_x x(kT) - K_I q(kT)
$$

## Dimensions
| Quantity | Dimension |
|---|---|
| $x$ | $\mathbb{R}^n$ |
| $u$ | $\mathbb{R}^m$ |
| $y$ | $\mathbb{R}^p$ |
| $q$ | $\mathbb{R}^p$ |

## Design Flow
1. Form $G_z$ and $H_z$.
2. Check controllability of the augmented pair.
3. Choose augmented closed-loop poles.
4. Solve for $K_z$.
5. Split into $K_x$ and $K_I$.

## Links
- [[Integral Action for Disturbance Rejection]]
- [[Non-Zero Regulation with Integral Action]]
- [[Sinusoidal Tracking by Augmentation]]

## Visual Placeholders
![[Augmented State Matrix for Integral Action.png|400]]
