# Observability

## Core Idea
- **Observability** asks whether the initial system state can be reconstructed from measured outputs and known inputs.
- In discrete time, this is based on **sampled outputs** and **input sequences**.

## Definition
- A system is **observable** if any initial state $x(0)$ can be uniquely determined from knowledge of:
  - the output sequence
  - the input sequence
  - a finite number of sample instants

## State-Space Context
For
$$
x(kT+T)=Gx(kT)+Hu(kT)
$$
$$
y(kT)=Cx(kT)+Du(kT)
$$
the observability test uses the pair $(G,C)$.

## Observability Matrix
The observability matrix is
$$
\mathcal{O}_{GC}=\begin{bmatrix}
C \\
CG \\
CG^2 \\
\vdots \\
CG^{n-1}
\end{bmatrix}
$$

## Test
- A system of order $n$ is completely observable iff
$$
\operatorname{rank}(\mathcal{O}_{GC})=n
$$

## Output-Sequence Interpretation
If the input is zero, then the output sequence becomes:
$$
y(0)=Cx(0)
$$
$$
y(1)=CGx(0)
$$
$$
y(2)=CG^2x(0)
$$
$$
\vdots
$$
$$
y(k)=CG^k x(0)
$$

## Why Rank Matters
- With $n$ states, we need $n$ linearly independent equations to identify $x(0)$ uniquely.
- That is exactly why full rank of $\mathcal{O}_{GC}$ is required.

## Practical Meaning
- If a state is **unobservable**, the controller cannot infer its behaviour from the measured output.
- That makes stabilization or estimator design harder or impossible for that mode.

## Links
- [[Controllability]]
- [[Discrete-Time Controllability and Observability Nuances]]
- [[Discrete State Feedback]]

## Visual Placeholders
![[Observability Output Stack.png|400]]
