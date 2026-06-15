1. If two blocks $G_1(s)$ and $G_2(s)$ are connected in series, what is the resulting transfer function?
A) $G_1(s) + G_2(s)$
B) $G_1(s) / G_2(s)$
C) $G_1(s) \cdot G_2(s)$
D) $1 / (G_1(s) + G_2(s))$

2. What is the purpose of the state vector $x(t)$ in a state-space model?
A) It represents the input applied to the system.
B) It represents the output of the system.
C) It contains the minimum set of variables that fully describe the system's dynamics.
D) It is the matrix that relates the input to the output.

3. For a Linear Time-Invariant (LTI) system to be BIBO stable, where must the poles of its transfer function be located in the s-plane?
A) On the imaginary axis.
B) In the Right-Half Plane (RHP).
C) In the Left-Half Plane (LHP).
D) At the origin.

4. For an LTI system $\dot{x} = Ax$, which equation must be satisfied for a symmetric, positive definite matrix $P$ to exist, given a positive definite matrix $Q$?
A) $A^T P + PA = Q$
B) $A P + P A^T = -Q$
C) $A^T P + PA = -Q$
D) $P A P = -Q$

5. A system whose mathematical model explicitly depends on time, such as $\dot{x} = A(t)x + B(t)u$, is categorized as:
A) Time-invariant
B) Time-varying
C) Linear
D) Nonlinear

6. In the linearization of a nonlinear system around an equilibrium point $(\bar{x}, \bar{u})$, the Jacobian matrices are evaluated at which location?
A) Any arbitrary point in the state space.
B) The origin $(0, 0)$.
C) The specific equilibrium point $(\bar{x}, \bar{u})$.
D) The point where the system is most unstable.

7. Why are difference equations, rather than differential equations, used for implementing controllers and plant models in digital computers?
A) Computers cannot perform continuous-time calculations.
B) Differential equations are only for linear systems.
C) Computers operate in discrete time with finite sampling periods.
D) Difference equations are always more accurate than differential equations.

8. In the context of signal reconstruction, what is the primary trade-off when using a higher-order polynomial hold compared to a Zero Order Hold (ZOH)?
A) Higher order holds are less accurate.
B) Higher order holds introduce more computational complexity but less delay.
C) Higher order holds provide more accurate reconstruction but introduce more delay/lag.
D) Higher order holds require more past input values but reduce the sampling rate requirement.

9. How can aliasing affect a digital control system's performance?
A) It improves the signal-to-noise ratio by filtering high frequencies.
B) It may cause the controller to misinterpret high-frequency noise as low-frequency dynamics.
C) It ensures the sampling frequency is always an integer multiple of the signal frequency.
D) It guarantees that the reconstructed signal is perfectly smooth.

10. The unilateral $\mathcal{Z}$ transform of a sequence $x[k]$ is defined as which of the following summations?
A) $\sum_{k=-\infty}^{\infty} x[k]z^{k}$
B) $\sum_{k=0}^{\infty} x[k]z^{-k}$
C) $\sum_{k=0}^{\infty} x[k]z^{k}$
D) $\sum_{k=1}^{\infty} x[k]z^{-k}$

11. What is the difference between "reachability" and "null controllability" in a discrete-time system?
A) Reachability means moving from any state to the zero state; null controllability means moving from zero to any state.
B) Reachability means moving from the zero state to any desired state; null controllability means moving from any initial state to the zero state.
C) Reachability applies only to linear systems, while null controllability applies to nonlinear systems.
D) There is no difference; they are identical for all LTI systems.

12. In a state-space control system, what is the primary purpose of having an observable system?
A) To ensure that any state can be reached using an input.
B) To allow for the unique reconstruction of the initial state from the observed output sequence and input sequence.
C) To guarantee that the system will be stable.
D) To minimize the control effort needed to achieve a target state.

13. According to the Internal Model Principle, what must a controller contain to ensure asymptotic rejection of a sinusoidal disturbance?
A) A single integrator.
B) A model of the sinusoidal disturbance dynamics.
C) A high-gain proportional term.
D) A lead compensator.

14. When adding integral action to a state-space controller for disturbance rejection, how is the integral state $q(kT)$ typically updated?
A) $q(kT+T) = q(kT) + u(kT)$
B) $q(kT+T) = q(kT) + y(kT)$
C) $q(kT+T) = q(kT) \cdot y(kT)$
D) $q(kT+T) = y(kT)$

15. A symmetric matrix $P$ is considered positive definite ($P \succ 0$) if:
A) All its eigenvalues are non-negative.
B) All its eigenvalues are strictly positive.
C) Its determinant is zero.
D) Its trace is zero.

16. In Model Predictive Control (MPC), what is the "receding horizon" principle?
A) The controller solves the optimization problem once for the entire lifetime of the system.
B) The controller applies the entire optimal control sequence calculated for the horizon.
C) The controller solves an optimization problem over a finite horizon, applies only the first input, and then re-solves the problem at the next time step.
D) The controller increases the prediction horizon length at every time step.

17. In a Kalman Filter, what does the optimal Kalman gain $K_k$ balance between?
A) The process noise and the sampling rate.
B) The model prediction and the noisy measurement.
C) The system dynamics and the input signal.
D) The prediction error and the control effort.

18. When designing an observer-based controller, what is a common rule of thumb for the placement of observer poles relative to controller poles?
A) Observer poles should be slower than controller poles.
B) Observer poles should be placed at the same location as controller poles.
C) Observer poles should be placed 5–10 times faster (closer to the origin) than controller poles.
D) Observer poles should be placed in the Right-Half Plane.

19. For the discrete-time LQR solution to guarantee closed-loop stability, which pair must be observable?
A) $(G, H)$
B) $(G, V)$ where $Q = V^T V$
C) $(G, K)$
D) $(H, V)$

20. Under the Tustin Bilinear Transform, where is the imaginary ($j\omega$) axis of the s-plane mapped in the z-plane?
A) To the origin.
B) To the unit circle ($|z|=1$).
C) To the entire interior of the unit circle.
D) To infinity.
