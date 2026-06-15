# Multiple Choice Questions

1. What is the transfer function of two blocks $G_1$ and $G_2$ connected in parallel?
A) $G_2 G_1$
B) $G_1 / (1 + G_2 G_1)$
C) $G_2 + G_1$
D) $G_2 - G_1$

2. In the standard LTI state-space representation $\dot{x} = Ax + Bu$ and $y = Cx + Du$, what are the dimensions of the state matrix $A$ for a system with $n$ states?
A) $n \times m$
B) $p \times n$
C) $n \times n$
D) $p \times m$

3. What is the condition for an LTI system $\dot{x} = Ax$ to be considered internally stable?
A) All poles of the transfer function have negative real parts.
B) The real parts of all eigenvalues of matrix $A$ are strictly negative.
C) The output $y(t)$ remains bounded for any bounded input $u(t)$.
D) All poles of the transfer function are on the imaginary axis.

4. According to Lyapunov's direct method, if for a positive definite energy function $V(x)$, its time derivative $\dot{V}(x)$ is strictly negative ($\dot{V}(x) < 0$), the equilibrium point is:
A) Unstable
B) Lyapunov stable but not asymptotically stable
C) Asymptotically stable
D) Marginally stable

5. A system $G$ is considered linear if and only if it satisfies which of the following properties?
A) Stability and Time-Invariance
B) Additivity and Homogeneity
C) Continuity and Differentiability
D) Boundedness and Causality

6. In the linearization of a nonlinear system $\dot{x} = f(x, u)$ around an equilibrium point $(\overline{x}, \overline{u})$, the state matrix $A$ is derived by taking the partial derivative of the system functions with respect to which variable?
A) The input vector $u$
B) The state vector $x$
C) The output vector $y$
D) The equilibrium point $\overline{x}$

7. The approximation $\dot{x}(kT) \approx \frac{x(kT + T) - x(kT)}{T}$ is a first-order Taylor series approximation to the derivative known as:
A) Euler Backward method
B) Trapezoidal rule
C) Euler Forward method
D) Runge-Kutta method

8. What is the primary characteristic of a Zero Order Hold (ZOH) in a discrete-time control system?
A) It linearly extrapolates the signal using the current and previous sample.
B) It holds the sampled value constant for the entire sampling period $T$.
C) It uses an $n$th order polynomial to reconstruct the signal.
D) It uses an infinitesimal time step to approximate the derivative.

9. According to the Nyquist Criterion, to avoid aliasing and allow for unambiguous reconstruction of a signal, the sampling frequency $f_s$ must be:
A) Equal to the highest signal frequency $f$
B) Less than twice the highest signal frequency $f$
C) Greater than twice the highest signal frequency $f$
D) At least equal to the signal frequency $f$

10. The mapping between the $s$-plane (Laplace transform) and the $z$-plane ($\mathcal{Z}$ transform) is defined by which relationship?
A) $z = e^{-sT}$
B) $z = e^{sT}$
C) $z = \frac{1}{T}\ln(s)$
D) $z = sT$

11. A discrete-time LTI system of order $n$ with matrices $G$ and $H$ is completely state controllable if and only if the controllability matrix $\mathcal{C}_{GH}$ satisfies which condition?
A) $\operatorname{rank}(\mathcal{C}_{GH}) < n$
B) $\operatorname{rank}(\mathcal{C}_{GH}) = n$
C) $\det(G) = 0$
D) $\det(H) = 1$

12. In a discrete-time system defined by matrices $G$ and $C$, what is the requirement for the system to be completely observable?
A) $\operatorname{rank}(\mathcal{C}_{GH}) = n$
B) $\operatorname{rank}(\mathcal{O}_{GC}) = n$
C) $\det(G) = 1$
D) $C = 0$

13. According to the Internal Model Principle, if a controller is required to achieve asymptotic tracking of a constant step reference, what must the controller contain?
A) A double integrator
B) A sinusoid model
C) A single integrator model
D) A high-gain proportional controller

14. What is the primary purpose of introducing integral action into a control loop?
A) To increase the bandwidth of the system.
B) To remove steady-state error caused by constant disturbances.
C) To make the system more responsive to fast-changing signals.
D) To reduce the complexity of the controller.

15. In the Linear Quadratic Regulator (LQR) problem, the cost function $J$ is minimized subject to the system dynamics. What do the matrices $Q$ and $R$ in the cost function $J = \sum_{k=0}^{\infty} (x(k)^\top Q x(k) + u(k)^\top R u(k))$ represent?
A) $Q$ is the input penalty matrix and $R$ is the state penalty matrix.
B) $Q$ is the state penalty matrix and $R$ is the control penalty matrix.
C) $Q$ and $R$ are the system matrices $G$ and $H$.
D) $Q$ is the state matrix $A$ and $R$ is the input matrix $B$.

16. What is the primary difference between the receding horizon strategy used in Model Predictive Control (MPC) and the standard LQR approach?
A) MPC uses an infinite horizon, while LQR uses a finite horizon.
B) MPC solves a finite-horizon optimization problem at each step and applies only the first control input.
C) LQR handles constraints explicitly, while MPC does not.
D) MPC uses a static gain calculated offline, whereas LQR performs online optimization.

17. Compared to a standard Luenberger Observer, what is a key advantage of the Kalman Filter?
A) It uses constant gain for all systems.
B) It is designed to ignore all sensor noise.
C) It optimally balances model prediction and noisy measurements using noise covariance matrices $Q$ and $R$.
D) It is only applicable to nonlinear systems.

18. According to the Separation Principle, when designing an observer-based controller, how should the controller gain $K$ and the observer gain $L$ be determined?
A) They must be designed together simultaneously to ensure stability.
B) The controller gain $K$ and observer gain $L$ can be designed independently.
C) The observer gain $L$ must be designed first, then the controller gain $K$ must be adjusted to compensate.
D) The gains are always identical in a separation-based design.

19. When tuning an LQR controller, if the states are converging to their target values too slowly, what is a recommended action?
A) Increase the elements in the control penalty matrix $R$ relative to $Q$.
B) Decrease the elements in the state penalty matrix $Q$ relative to $R$.
C) Increase the elements in the state penalty matrix $Q$ relative to $R$.
D) Decrease the sampling time $T$.

20. The Tustin Bilinear Transform is used to convert a continuous-time transfer function $G_c(s)$ into a discrete-time equivalent $G_d(z)$. What is the substitution rule for $s$ in this transform?
A) $s = \frac{2}{T} \frac{z-1}{z+1}$
B) $s = \frac{T}{2} \frac{z+1}{z-1}$
C) $s = \frac{1}{T} \frac{z-1}{z+1}$
D) $s = \frac{2}{T} \frac{z+1}{z-1}$
