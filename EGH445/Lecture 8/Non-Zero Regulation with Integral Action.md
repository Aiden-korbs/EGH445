# Non-Zero Regulation with Integral Action

## Core Idea
- For a constant desired output $\bar{y}$, define the error:
$$
e(kT) = \bar{y} - y(kT)
$$
- Then integrate the error rather than the output:
$$
q(kT+T) = q(kT) + e(kT)
$$

## Augmented Dynamics
$$
x(kT+T) = Gx(kT) + Hu(kT)
$$
$$
q(kT+T) = q(kT) + \bar{y} - Cx(kT)
$$

Define
$$
z(kT) = \begin{bmatrix}x(kT)\\ q(kT)\end{bmatrix}
$$

Then
$$
z(kT+T) =
\underbrace{\begin{bmatrix}
G & 0_{n\times p}\\
-C & I_{p\times p}
\end{bmatrix}}_{G_z}
z(kT)
+
\underbrace{\begin{bmatrix}
H\\
0_{p\times m}
\end{bmatrix}}_{H_z}
u(kT)
+
\underbrace{\begin{bmatrix}
0_{n\times p}\\
I_{p\times p}
\end{bmatrix}}_{E_z}
r(kT)
$$

## Control Law
$$
u(kT) = -K_x x(kT) - K_I q(kT)
$$

## Result
- Integral action can:
  - drive steady-state error to zero for constant references
  - reject constant input disturbances at the same time

## Practical Meaning
- This is more robust than relying only on a feedforward gain like [[Feedforward Disturbance Compensation]].

## Links
- [[Augmented System for Integral Action]]
- [[Tracking vs Regulation]]
- [[Internal Model Principle]]

## Visual Placeholders
![[Error Integrator for Constant Reference.png|400]]
