## 1. Block Diagram Algebra
**Question:** In a standard negative feedback configuration with forward path transfer function $G_1$ and feedback path transfer function $G_2$, what is the overall transfer function?

**Answer:** The overall transfer function for a negative feedback loop is given by:
$$\frac{G_1}{1 + G_1G_2}$$

---

## 2. State-Space Modelling
**Question:** Given a linear time-invariant (LTI) state-space system defined by $\dot{x} = Ax + Bu$ and $y = Cx + Du$, what are the required dimensions for the state matrix $A$, input matrix $B$, output matrix $C$, and direct feedthrough matrix $D$, if the system has $n$ states, $m$ inputs, and $p$ outputs?

**Answer:** For a system with $n$ states, $m$ inputs, and $p$ outputs:
- The state matrix $A$ is $n \times n$.
- The input matrix $B$ is $n \times m$.
- The output matrix $C$ is $p \times n$.
- The direct feedthrough matrix $D$ is $p \times m$.

---

## 3. LTI System Stability
**Question:** What is the difference between BIBO (Bounded-Input-Bounded-Output) stability and internal stability for a Linear Time-Invariant (LTI) system?

**Answer:** BIBO stability is an external stability property where every bounded input results in a bounded output, which occurs if all poles of the transfer function have negative real parts. Internal stability is a stronger property where all internal states decay to zero for any initial condition, which occurs if and only if all eigenvalues of the state matrix $A$ have negative real parts. A system can be BIBO stable but internally unstable if there are unstable pole-zero cancellations.

---

## 4. Lyapunov Stability Criteria
**Question:** For an LTI system $\dot{x} = Ax$, how can the Lyapunov equation $A^T P + PA = -Q$ be used to determine stability?

**Answer:** If we can find a symmetric, positive definite matrix $P$ for a given symmetric, positive definite matrix $Q$, then the system is asymptotically stable. This condition is met if and only if all eigenvalues of the matrix $A$ have strictly negative real parts.

---

## 5. Linear vs Nonlinear Systems
**Question:** What are the two properties required for a system to be considered linear, and how does this contrast with nonlinear systems?

**Answer:** A linear system must satisfy the principle of superposition, which consists of two properties: **additivity** ($G(u_1 + u_2) = G(u_1) + G(u_2)$) and **homogeneity** ($G(\alpha u_1) = \alpha G(u_1)$). In contrast, nonlinear systems do not satisfy these properties, often requiring numerical approximations for solutions and typically having stability that is only determined locally.

---

## 6. Jacobian Matrices in Linearisation
**Question:** Given a nonlinear system $\dot{x} = f(x, u)$, how are the state matrix $A$ and input matrix $B$ for the linearized incremental model $\dot{\delta x} = A\delta x + B\delta u$ defined?

**Answer:** The matrices are defined by the Jacobians of the function $f$ evaluated at the equilibrium point $(\overline{x}, \overline{u})$:
- $A = \left( \frac{\partial f}{\partial x} \right)^T \Bigg|_{x=\overline{x}, u=\overline{u}}$
- $B = \left( \frac{\partial f}{\partial u} \right)^T \Bigg|_{x=\overline{x}, u=\overline{u}}$

---

## 7. Difference Equations
**Question:** How can the Euler Forward method be used to derive a difference equation from a continuous-time differential equation $\dot{x} = f(x, u)$?

**Answer:** The Euler Forward method approximates the derivative with a finite change in time $T$: $\dot{x}(kT) \approx \frac{x(kT + T) - x(kT)}{T}$. By substituting this into the differential equation, we get $x(kT + T) \approx x(kT) + T f(x(kT), u(kT))$. This allows for the construction of discrete state-space equations in the form $x(k+1) = Gx(k) + Hu(k)$.

---

## 8. Zero Order Hold and Data Hold
**Question:** What is the mathematical definition of a Zero Order Hold (ZOH) and what is its Laplace transform?

**Answer:** A Zero Order Hold (ZOH) generates a continuous-time signal by holding the sampled value $u(kT)$ constant over the entire sampling interval $T$, such that $u(kT + \tau) = u(kT)$ for $0 \le \tau < T$. Its Laplace transform is given by:
$$U(s) = \frac{1 - e^{-Ts}}{s}$$

---

## 9. Aliasing and Nyquist Criterion
**Question:** Explain the concept of aliasing and state the Nyquist Criterion for signal reconstruction.

**Answer:** Aliasing is a phenomenon that occurs when a continuous-time signal is sampled at a rate that is too slow, causing multiple continuous-time frequencies to result in the same discrete-time sampled sequence, leading to incorrect signal reconstruction. According to the Nyquist Criterion, to reconstruct a signal of frequency $f$ unambiguously, the sampling frequency $f_s$ must satisfy $f < \frac{f_s}{2}$, where $\frac{f_s}{2}$ is known as the Nyquist rate.

---

## 10. Z Transform
**Question:** What is the relationship between the Laplace transform $X^*(s)$ of a sampled signal $x^*(t)$ and its unilateral $\mathcal{Z}$ transform $X(z)$?

**Answer:** The $\mathcal{Z}$ transform is the Laplace transform of the sampled signal $x^*(t) = \sum_{k=0}^{\infty} x[k]\delta(t-kT)$ under the change of variable $z = e^{sT}$. Specifically, $X(z) = \sum_{k=0}^{\infty} x[k]z^{-k}$, which relates to $X^*(s) = \sum_{k=0}^{\infty} x[k]e^{-kTs}$ via the mapping $z^{-1} = e^{-sT}$.

---

## 11. Controllability
**Question:** How can you determine if a discrete-time LTI system $x(k+1) = Gx(k) + Hu(k)$ of order $n$ is completely state controllable?

**Answer:** A system is completely state controllable if the controllability matrix $\mathcal{C}_{GH} = \begin{bmatrix} H & GH & G^2H & \cdots & G^{n-1}H \end{bmatrix}$ has a rank equal to $n$. For square controllability matrices, this is equivalent to checking if $\det(\mathcal{C}_{GH}) \neq 0$.

---

## 12. Observability
**Question:** What is the observability matrix for a discrete-time system $x(k+1) = Gx(k) + Hu(k)$ with output $y(k) = Cx(k) + Du(k)$, and what is the condition for complete observability?

**Answer:** The observability matrix for the pair $(G, C)$ is $\mathcal{O}_{GC} = \begin{bmatrix} C \\ CG \\ CG^2 \\ \vdots \\ CG^{n-1} \end{bmatrix}$. A system of order $n$ is completely observable if and only if $\operatorname{rank}(\mathcal{O}_{GC}) = n$, meaning we have $n$ linearly independent equations to uniquely identify the initial state $x(0)$ from the output sequence.

---

## 13. Internal Model Principle
**Question:** According to the Internal Model Principle, what must a controller contain to achieve asymptotic tracking of a reference signal or rejection of a disturbance signal?

**Answer:** To achieve asymptotic tracking or disturbance rejection, the controller must include a model of the signal class within its structure. For example, to track a step reference, the controller must incorporate the dynamics of a single integrator, $\frac{1}{z-1}$. To track a ramp, it requires a double-integrator-type model, $\frac{1}{(z-1)^2}$, and to track sinusoids, it requires oscillatory internal dynamics.

---

## 14. Integral Action for Disturbance Rejection
**Question:** How is integral action implemented in a discrete-time controller to achieve disturbance rejection, and what is its primary benefit?

**Answer:** Integral action is implemented by introducing a new state $q$ that integrates the output or error over time, for example: $q(k+1) = q(k) + y(k)$. The control law is then modified to include this state: $u(k) = -K_x x(k) - K_I q(k)$. Its primary benefit is the removal of steady-state error caused by constant (step) disturbances by accumulating the error until the output is driven back to the desired setpoint.

---

## 15. Optimal Control Fundamentals
**Question:** In the context of the Linear Quadratic Regulator (LQR) problem, define the infinite-horizon cost function $J$ and explain the roles of the matrices $Q$ and $R$.

**Answer:** The infinite-horizon LQR cost function is defined as:
$$J = \sum_{k=0}^{\infty} \left( x(kT)^\top Q x(kT) + u(kT)^\top R u(kT) \right)$$
- The matrix $Q$ is the state penalty matrix, which must be positive semi-definite ($Q \succeq 0$). It weights the deviation of the states from the origin.
- The matrix $R$ is the control penalty matrix, which must be positive definite ($R \succ 0$). It weights the control effort required.
The relative sizes of $Q$ and $R$ define the performance trade-off between state tracking and control effort.

---

## 16. Model Predictive Control MPC
**Question:** Contrast Model Predictive Control (MPC) with the Linear Quadratic Regulator (LQR) in terms of horizon, constraint handling, and computational complexity.

**Answer:**
- **Horizon:** LQR solves an infinite-horizon optimal control problem, whereas MPC solves a finite-horizon optimization problem at each time step (known as the prediction horizon).
- **Constraint Handling:** LQR does not explicitly handle constraints (saturation can break its guarantees), while MPC can naturally incorporate input, state, and rate-of-change constraints as part of its optimization.
- **Computational Complexity:** LQR has low computational complexity (offline gain calculation, online: $u = -Kx$), whereas MPC has higher complexity because it must solve an optimization problem online at every time step.

---

## 17. The Kalman Filter
**Question:** Why is the Kalman Filter considered an optimal estimator compared to the standard Luenberger Observer in environments with process and measurement noise?

**Answer:** Unlike the Luenberger Observer, which uses a constant gain chosen by pole placement and assumes a deterministic model, the Kalman Filter explicitly incorporates the statistical characteristics (covariances $Q$ and $R$) of process and measurement noise. It uses a recursive predictor-corrector approach to calculate an optimal time-varying gain $K_k$ that minimizes the estimated error covariance $P_k$, thereby optimally balancing the reliability of the system model versus the noisy measurements.

---

## 18. Separation Principle
**Question:** What is the Separation Principle in the context of observer-based control, and how does it simplify the design process?

**Answer:** The Separation Principle states that for an observer-based controller ($u(kT) = -K\hat{x}(kT)$), the controller gain $K$ and the observer gain $L$ can be designed independently. This is because the combined closed-loop system matrix is block upper triangular, meaning the set of closed-loop eigenvalues is simply the union of the controller poles ($\text{eig}(G - HK)$) and the observer error poles ($\text{eig}(G - LC)$). This simplifies design by allowing one to first design $K$ (assuming full state feedback) and then design $L$ separately to ensure fast error convergence.

---

## 19. LQR Tuning Q and R
**Question:** In LQR tuning, why is the observability of the pair $(G, V)$ (where $Q = V^\top V$) important for guaranteeing closed-loop stability?

**Answer:** The observability of $(G, V)$ ensures that any unstable behavior in the system will eventually manifest in the states that are penalized by the cost function $Q$. If $(G, V)$ is observable, the optimization process will "see" the growing instability through the cost $x^\top Q x$ and will be forced to choose control inputs that drive the states back to zero to minimize the overall cost $J$, thus guaranteeing stability.

---

## 20. Tustin Bilinear Transform
**Question:** How does the Tustin Bilinear Transform map the s-plane to the z-plane, and what is its primary advantage regarding stability?

**Answer:** The Tustin Bilinear Transform uses the substitution $s \leftarrow \frac{2}{T}\frac{z-1}{z+1}$ to map the continuous-time s-plane to the discrete-time z-plane. Its primary advantage is that it maps the entire left-half of the s-plane into the interior of the unit circle in the z-plane, which ensures that stability is preserved (a stable continuous-time system will always result in a stable discrete-time system).
