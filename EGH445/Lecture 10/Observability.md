# Observability

← Back to [[State Estimation: Observers and Output Feedback]]

## Definition

A discrete-time system $x(kT+T) = Gx(kT) + Hu(kT)$, $y(kT) = Cx(kT)$, is **completely observable** if, for any initial time $k_0T$, the initial state $x(k_0T)$ can be uniquely determined from the knowledge of the input sequence $u(kT)$ and the output sequence $y(kT)$ over a finite number of steps.

## Why Observability Matters

For observer design, the ability to arbitrarily assign eigenvalues of $(G - LC)$ depends on $(G, C)$ being observable — analogous to how [[Pole Placement]] requires controllability of $(G, H)$.

## Observability Test

### Observability Matrix

$$\mathcal{O} = \begin{bmatrix} C \\ CG \\ CG^2 \\ \vdots \\ CG^{n-1} \end{bmatrix}$$

### Test Procedure

1. Construct the observability matrix $\mathcal{O}$
2. Calculate its rank using `numpy.linalg.matrix_rank(O)` or `rank(ObsvMatrix)` in MATLAB
3. If $\mathcal{O}$ is square, it is full rank iff $\det(\mathcal{O}) \neq 0$
4. If $\text{rank}(\mathcal{O}) < n$, the system is not completely observable

### Condition

The pair $(G, C)$ is completely observable **if and only if** $\text{rank}(\mathcal{O}) = n$, where $n$ is the dimension of the state vector.

## Vehicle Example

System parameters: $m = 1$, $b = 0.5$, $T = 0.1$

$$G = \begin{bmatrix} 1 & 0.0975 \\ 0 & 0.9512 \end{bmatrix}, \quad H = \begin{bmatrix} 0.0049 \\ 0.0975 \end{bmatrix}$$

### Case 1: Position Measurement

$$C_1 = \begin{bmatrix} 1 & 0 \end{bmatrix}$$

$$\mathcal{O}_1 = \begin{bmatrix} C_1 \\ C_1G \end{bmatrix} = \begin{bmatrix} 1 & 0 \\ 1 & 0.0975 \end{bmatrix}$$

$$\det(\mathcal{O}_1) = 0.0975 \neq 0, \quad \text{rank} = 2$$

**System is observable** when measuring position.

### Case 2: Velocity Measurement

$$C_2 = \begin{bmatrix} 0 & 1 \end{bmatrix}$$

$$\mathcal{O}_2 = \begin{bmatrix} C_2 \\ C_2G \end{bmatrix} = \begin{bmatrix} 0 & 1 \\ 0 & 0.9512 \end{bmatrix}$$

$$\det(\mathcal{O}_2) = 0, \quad \text{rank} = 1$$

**System is NOT observable** when measuring velocity only.

## Key Takeaway

Not all output configurations yield an observable system. The choice of sensors directly determines whether states can be estimated — and therefore whether observer-based control is possible.
