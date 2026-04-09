# Pole Placement Gain Methods

## Goal
- Find the gain vector
$$
K=\begin{bmatrix}k_0 & k_1 & \dots & k_{n-1}\end{bmatrix}
$$
such that the eigenvalues of
$$
G-HK
$$
match the desired closed-loop pole locations.

## Method 1: Equating coefficients
### Idea
- Form the actual characteristic equation:
$$
\det(zI-(G-HK))=0
$$
- Form the desired characteristic equation from chosen poles.
- Equate coefficients of like powers of $z$ and solve for $k_0,\dots,k_{n-1}$.

### Best for
- Low-order systems
- Small systems where the simultaneous equations are manageable by hand

### Notes
- This is the method used directly in the 2-state special case of [[Example 1 - Mass Spring Damper Direct Design]].

## Method 2: Phase-variable form
### Idea
- If the system is already in **phase variable** or **companion form**, the gains can be read directly from the difference between:
  - desired characteristic coefficients
  - actual characteristic coefficients

### Typical companion structure
$$
\tilde{G}=
\begin{bmatrix}
0 & 1 & 0 & \cdots & 0 \\
0 & 0 & 1 & \cdots & 0 \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
0 & 0 & 0 & \cdots & 1 \\
-a_0 & -a_1 & -a_2 & \cdots & -a_{n-1}
\end{bmatrix},
\qquad
\tilde{H}=
\begin{bmatrix}
0\\
0\\
\vdots\\
0\\
1
\end{bmatrix}
$$

### Gain relation
- In companion form, the transformed gain is obtained directly from the coefficient differences:
$$
K_z=\begin{bmatrix}\beta_0-a_0 & \beta_1-a_1 & \dots & \beta_{n-1}-a_{n-1}\end{bmatrix}
$$
where the $\beta_i$ terms come from the desired characteristic equation.

## Method 3: State transformation
### Idea
- If the original system is not in phase-variable form, transform it into one that is.

### Transformation
Let
$$
z=P^{-1}x
$$
or equivalently
$$
x=Pz
$$

Then:
$$
\tilde{G}=P^{-1}GP,\qquad \tilde{H}=P^{-1}H
$$

### Workflow
1. Find a suitable transformation matrix $P$.
2. Transform the system into phase-variable form.
3. Compute the transformed gain $K_z$ using Method 2.
4. Transform back to the original coordinates:
$$
K=K_zP^{-1}
$$

## Choosing a Method
| Method | Best Use |
|---|---|
| Equating coefficients | low-order hand calculations |
| Phase-variable form | system already in companion form |
| Transformation | higher-order or awkward system form |

## Links
- [[Discrete State Feedback]]
- [[State Feedback Design Procedure]]
- [[Example 1 - Mass Spring Damper Direct Design]]

## Visual Placeholders
![[Companion Form Structure.png|400]]
![[Transformation to Companion Form.png|400]]
