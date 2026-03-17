← Back to [[Week 2 Workshop - System Response and Stability]]

# B747 Aircraft Model — 6DOF

## Overview
- Running Example 1 for EGH445 Workshop Week 2.
- A **6 Degree-of-Freedom (6DOF)** nonlinear aircraft model, **linearised** about an equilibrium point using MATLAB's Model Lineariser.
- Linearised form: $\tilde{x} = A\tilde{x} + B\tilde{u}$ about equilibrium $\bar{x}$.

> **Important:** $A$ and $B$ matrix values depend on **aircraft type** (physical construction) and **airspace environment** (pressure, temperature, etc.).

![[B747 6DOF Diagram.png|400]]

## State Variables

| Symbol | Description |
| :--- | :--- |
| $x, y, z$ | Position coordinates |
| $u, v, w$ | Velocity coordinates |
| $p$ | Roll rate |
| $q$ | Pitch rate |
| $r$ | Yaw rate |
| $\phi$ | Roll angle |
| $\theta$ | Pitch angle |
| $\psi$ | Yaw angle |
| $\beta$ | Side-slip angle |
| $\alpha$ | Angle of attack |

## Longitudinal Dynamics ('up/down')

**Scenario:** Aircraft perturbed from equilibrium with initial angle of attack perturbation.

**Given:**

$$\begin{bmatrix} \Delta\dot{u} \\ \Delta\dot{\alpha} \\ \Delta\dot{q} \\ \Delta\dot{\theta} \end{bmatrix} = \begin{bmatrix} -0.0212 & 0.0466 & 0 & -32.174 \\ -0.2229 & -0.5839 & 262.472 & 0 \\ 0.0001 & -0.0018 & -0.5015 & 0 \\ 0 & 0 & 1 & 0 \end{bmatrix} \begin{bmatrix} \Delta u \\ \Delta\alpha \\ \Delta q \\ \Delta\theta \end{bmatrix} + \begin{bmatrix} 0 \\ -0.0340 \\ -0.5746 \\ 0 \end{bmatrix} [\Delta\delta_e]$$

$$\bar{\Delta}x = \begin{bmatrix} 0 \\ 5 \\ 0 \\ 0 \end{bmatrix}, \qquad \bar{\Delta}u = [0]$$

> Note: Input matrix shown assumes constant/fixed thrust ($\Delta\delta_T = 0$).

## Steps: Longitudinal Stability Analysis

**Step 1 — Eigenvalues (Poles):**

$$\lambda_{1,2} = -0.55175 \pm 0.68686i \quad \text{(Short Period Mode)}$$

$$\lambda_{3,4} = -0.0015488 \pm 0.13802i \quad \text{(Phugoid Mode)}$$

**Step 2 — Stability Assessment:**
- All eigenvalues have **negative real parts** → system is [[Asymptotic Stability|asymptotically stable]].
- However, the phugoid mode is **very lightly damped** (near-zero real part) → very slow decay.

**Step 3 — Simulation Observations:**

| Sim Time | Observed Behaviour |
| :--- | :--- |
| $10\ \text{s}$ | Short period: pitches up/down; $\alpha$ and $q$ respond rapidly |
| $100\ \text{s}$ | Phugoid mode visible — slow oscillation in $\tilde{u}$ and $\theta$ |
| $1000\ \text{s}$ | Phugoid slowly decays; Lyapunov function $V(x) = x^T P x$ monotonically decreasing |

**Final Notes:**
- The [[Lyapunov Stability|Lyapunov function]] $V(x) = x^T P x$ decreases monotonically → consistent with asymptotic stability.
- Despite being stable, the phugoid mode has a very long settling time — relevant for flight control design.

## Lateral Dynamics ('left/right')
A similar linearised model governs **roll-yaw** and **left-right** motion. A similar eigenvalue/Lyapunov analysis can be conducted to study how the aircraft behaves laterally.

## MATLAB Code
```matlab
% Simulate initial condition response
[y, tOut, x] = initial(SysC, x0, t);

% Lyapunov function along trajectory
Q = eye(4);
P = lyap(A, Q);
V = zeros(length(tOut), 1);
for k = 1:length(tOut)
    V(k) = x(k,:) * P * x(k,:)';
end
plot(tOut, V, 'LineWidth', 1.5);
```

## Related Notes
- [[ODE General Solution]]
- [[Analytical Solution - Linear Systems]]
- [[State Transition Matrix]]
- [[Internal Stability]]
- [[Lyapunov Stability]]
- [[Asymptotic Stability]]
- [[Hodgkin-Huxley Neuron Model]]
