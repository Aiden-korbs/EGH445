## Purpose
To change the coordinate system of the state vector while maintaining the same input-output relationship (Transfer Function).

## Linear Transformation
Given an invertible matrix $T$, define a new state $z$:$$x = Tz$$
### New System Matrices
| Original | Transformed | Formula |
| :--- | :--- | :--- |
| $A$ | $A_z$ |$T^{-1}AT$ |
| $B$ | $B_z$ |$T^{-1}B$ |
| $C$ | $C_z$ |$CT$ |
| $D$ | $D_z$ |$D$ |

## Properties
***Eigenvalues**: The eigenvalues of $A$ and $A_z$ are identical.
* **Invariance**: The Transfer Function $H(s)$ remains unchanged.