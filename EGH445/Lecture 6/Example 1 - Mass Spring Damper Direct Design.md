# Example 1 - Mass Spring Damper Direct Design

## System
The lecture example uses the continuous-time model:
$$
\dot{x}(t)=
\begin{bmatrix}
0 & 1\\
-1 & -2
\end{bmatrix}x(t)+
\begin{bmatrix}
0\\
1
\end{bmatrix}u(t)
$$
$$
y(t)=
\begin{bmatrix}
1 & 0
\end{bmatrix}x(t)
$$

## Physical Meaning
- This is a **mass-spring-damper** system with:
  - damper $b=2$
  - mass $m=1$
  - spring $c=1$
- The measured output is the **displacement** state $x_1(t)$.

## Design Requirement
The lecture asks for direct design so that the closed-loop system has:
$$
\zeta=0.8,\qquad \omega_n=1.7\ \text{rad/s}
$$
for:
- $T=1$
- $T=0.1$

## General Approach
1. Start from the continuous-time state-space model.
2. Derive the exact discrete-time model.
3. Check controllability.
4. Use the design criteria to determine desired poles.
5. Construct the desired characteristic equation.
6. Solve for $K$.
7. Compare the resulting discrete response with continuous-time behaviour.

## Discrete Model for $T=1$
The lecture gives:
$$
x(kT+T)=
\begin{bmatrix}
0.7358 & 0.3679\\
-0.3679 & 0
\end{bmatrix}x(kT)+
\begin{bmatrix}
0.2642\\
0.3679
\end{bmatrix}u(kT)
$$
$$
y(kT)=
\begin{bmatrix}
1 & 0
\end{bmatrix}x(kT)
$$

### Controllability check
The controllability matrix is
$$
\mathcal{C}_{GH}=\begin{bmatrix}H & GH\end{bmatrix}
$$
and the lecture shows it is full rank, so state feedback can be used.

## Desired Pole Construction
For a second-order target, start with:
$$
s^2+2\zeta\omega_n s+\omega_n^2=0
$$
Then map the desired continuous poles into the $z$-plane using:
$$
z=e^{sT}
$$

## Gain Result for $T=1$
The lecture’s final gain for the original system is:
$$
K=\begin{bmatrix}1.00 & 0.55\end{bmatrix}
$$

## Discrete Model for $T=0.1$
The lecture gives:
$$
x(kT+T)=
\begin{bmatrix}
0.9953 & 0.0905\\
-0.0905 & 0.8144
\end{bmatrix}x(kT)+
\begin{bmatrix}
0.0047\\
0.0905
\end{bmatrix}u(kT)
$$
$$
y(kT)=
\begin{bmatrix}
1 & 0
\end{bmatrix}x(kT)
$$

## Gain Result for $T=0.1$
The lecture gives:
$$
K=\begin{bmatrix}1.79 & 0.72\end{bmatrix}
$$

## Important Observation
- The gain depends strongly on the sampling time.
- Even when the design criteria are the same, the discrete controller changes because the discrete plant changes.

## Scenario
### Scenario
Design a digital state-feedback controller for a mass-spring-damper system using direct design.

### Given
- Continuous-time state-space model
- Sampling time $T$
- Desired $\zeta$ and $\omega_n$

### Steps
1. Compute the exact discrete matrices $G$ and $H$.
2. Check $\operatorname{rank}(\mathcal{C}_{GH})=n$.
3. Compute desired continuous poles from:
$$
s^2+2\zeta\omega_n s+\omega_n^2=0
$$
4. Map the poles into the $z$-plane using:
$$
z=e^{sT}
$$
5. Form the desired characteristic equation.
6. Solve for $K$ using one of the pole-placement methods.
7. Simulate the closed-loop response.

### Final Notes
- The example shows both a hand-solution path and a transformed-system path.
- For low-order systems, equating coefficients can be quickest.
- For higher-order or awkward forms, a transformation to companion form is cleaner.

## Links
- [[State Feedback Design Procedure]]
- [[Pole Placement Gain Methods]]
- [[Feedforward Gain for Reference Tracking]]

## Visual Placeholders
![[Mass Spring Damper Example.png|400]]
![[Example 1 Response Comparison.png|400]]
