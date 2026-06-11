# Integral Action in Discrete-Time Control

## Why Integral Action Is Used
- Integral action is introduced to:
  - reject **constant disturbances**
  - eliminate **steady-state error** for constant references

## Classical Insight
- A **Type 1** system has zero steady-state error to a step input.
- Adding an integrator effectively embeds step-reference dynamics into the controller.

## Output-Integrated Augmentation
- One augmentation form integrates the output:
$$
q(kT+T) = q(kT) + y(kT)
$$

- Define the augmented state:
$$
z(kT) \triangleq \begin{bmatrix} x(kT) \\ q(kT) \end{bmatrix}
$$

- Then:
$$
z(kT+T) =
\underbrace{\begin{bmatrix}
G & 0_{n\times p} \\
C & I_{p\times p}
\end{bmatrix}}_{G_z}
z(kT) +
\underbrace{\begin{bmatrix}
H \\
0_{p\times m}
\end{bmatrix}}_{H_z}
u(kT)
$$

$$
y(kT) =
\underbrace{\begin{bmatrix}
C & 0_{p\times p}
\end{bmatrix}}_{C_z}
z(kT)
$$

## Error-Integrated Augmentation
- For regulation to a constant reference, integrate the error instead:
$$
e(kT) = r(kT) - y(kT)
$$

$$
q(kT+T) = q(kT) + e(kT)
$$

- This gives:
$$
z(kT+T) =
\underbrace{\begin{bmatrix}
G & 0_{n\times p} \\
-C & I_{p\times p}
\end{bmatrix}}_{G_z}
z(kT)
+
\underbrace{\begin{bmatrix}
H \\
0_{p\times m}
\end{bmatrix}}_{H_z}
u(kT)
+
\underbrace{\begin{bmatrix}
0_{n\times p} \\
I_{p\times p}
\end{bmatrix}}_{E_z}
r(kT)
$$

## Controller Form
$$
u(kT) = -K_z z(kT) = -K_x x(kT) - K_I q(kT)
$$

- $K_I$ is the **integral gain**.

## Practical Issues
| Issue | Meaning |
|---|---|
| **Wind-up** | Integrator keeps accumulating error when the actuator saturates |
| **Anti-windup** | Limits or corrects the integral state to avoid poor transients |
| **Controllability issue** | Can appear if the original plant has zeros at $z = 1$ |
| **Degree of freedom requirement** | Need one control DOF per integrated output |

## Key Design Steps
1. Define the added integral state $q(kT)$.
2. Form the augmented system.
3. Check controllability of the augmented model.
4. Design $K_z$.
5. Implement the integrator carefully, including anti-windup where needed.

## Links
- [[Disturbances in Discrete-Time Control]]
- [[Tracking and Internal Model Principle]]
- [[Augmented Aircraft Model for Integral Action]]

## Visual Placeholders
![[Integral Action Architecture.png|400]]
![[Anti Windup Comparison.png|400]]
