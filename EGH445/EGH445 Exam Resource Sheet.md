
---

## 1. Core State-Space Modelling

### Continuous-Time State Space

For a general nonlinear system:

$$\dot{x}(t)=f(x(t),u(t))$$

$$y(t)=g(x(t),u(t))$$

For a continuous-time LTI system:

$$\dot{x}=Ax+Bu$$

$$y=Cx+Du$$

Dimensions for $n$ states, $m$ inputs, and $p$ outputs:

| Matrix | Size | Meaning |
|---|---:|---|
| $A$ | $n \times n$ | State dynamics |
| $B$ | $n \times m$ | Input-to-state coupling |
| $C$ | $p \times n$ | State-to-output coupling |
| $D$ | $p \times m$ | Direct input-to-output feedthrough |

The state vector should be the minimum set of variables required to fully describe future behaviour when the input is known. For a mass-spring-damper system, a common state is $x=[\text{position},\text{velocity}]^T$.

### Transfer Function From State Space

Assuming zero initial conditions:

$$H(s)=\frac{Y(s)}{U(s)}=C(sI-A)^{-1}B+D$$

Key facts:

- Poles are roots of $\det(sI-A)=0$.
- These roots are the eigenvalues of $A$ for a minimal realisation.
- Matrix order matters. Do not rearrange matrix products as if they commute.

### Block Diagram Rules

| Connection | Equivalent Transfer Function |
|---|---|
| Series | $G_1G_2$ |
| Parallel | $G_1+G_2$ |
| Negative feedback | $\dfrac{G_1}{1+G_1G_2}$ |
| Positive feedback | $\dfrac{G_1}{1-G_1G_2}$ |

---

## 2. System Response And Stability

### Continuous-Time LTI Response

For

$$\dot{x}=Ax+Bu$$

the analytical solution is:

$$x(t)=e^{At}x_0+\int_0^t e^{A(t-\tau)}Bu(\tau)d\tau$$

The matrix exponential $e^{At}$ governs the natural response. It can be found from:

$$e^{At}=\mathcal{L}^{-1}\{(sI-A)^{-1}\}$$

If $A$ is diagonalisable:

$$A=T\Lambda T^{-1}$$

$$e^{At}=Te^{\Lambda t}T^{-1}$$

### Stability Types

| Type | Meaning | Continuous-Time LTI Test |
|---|---|---|
| BIBO stability | Every bounded input gives bounded output | Transfer-function poles have $\Re(s)<0$ |
| Internal stability | All states decay to zero for every initial state | All eigenvalues of $A$ have $\Re(\lambda)<0$ |
| Asymptotic stability | State approaches equilibrium over time | Same as internal stability for LTI autonomous system |

Internal stability is stronger than BIBO stability. A system can be BIBO stable but internally unstable if unstable modes are hidden by pole-zero cancellation.

### Lyapunov Stability Test For LTI Systems

For

$$\dot{x}=Ax$$

use the Lyapunov equation:

$$A^TP+PA=-Q$$

If $Q=Q^T\succ0$ and there exists $P=P^T\succ0$, then the system is asymptotically stable. For continuous-time LTI systems, this is equivalent to all eigenvalues of $A$ having strictly negative real parts.

### Eigenvalue Response Memory Aid

| Eigenvalue Type | Response Behaviour |
|---|---|
| Real negative | Exponential decay |
| Real positive | Exponential growth |
| Complex with negative real part | Decaying oscillation |
| Complex with positive real part | Growing oscillation |
| Pure imaginary | Sustained oscillation, marginal case |
| Zero eigenvalue | Integrator-like or marginal behaviour |

---

## 3. Nonlinear Systems And Linearisation

### Linearity Conditions

A system is linear if it satisfies superposition:

$$G(u_1+u_2)=G(u_1)+G(u_2)$$

$$G(\alpha u)=\alpha G(u)$$

Nonlinear systems may have multiple equilibria and local stability properties. Stability near one equilibrium does not imply global stability.

### Equilibrium Point

For

$$\dot{x}=f(x,u)$$

an equilibrium $\bar{x}$ with input $\bar{u}$ satisfies:

$$0=f(\bar{x},\bar{u})$$

At equilibrium, states do not change if the input is held at $\bar{u}$.

### Linearisation Workflow

1. Find equilibrium by solving $0=f(\bar{x},\bar{u})$.
2. Define incremental variables $\delta x=x-\bar{x}$ and $\delta u=u-\bar{u}$.
3. Approximate using a first-order Taylor expansion.
4. Compute Jacobians at the equilibrium.
5. Write the incremental linear model.

For the state equation:

$$\delta\dot{x}=A\delta x+B\delta u$$

where:

$$A=\left.\frac{\partial f}{\partial x}\right|_{\bar{x},\bar{u}}$$

$$B=\left.\frac{\partial f}{\partial u}\right|_{\bar{x},\bar{u}}$$

For the output equation:

$$\delta y=C\delta x+D\delta u$$

where:

$$C=\left.\frac{\partial g}{\partial x}\right|_{\bar{x},\bar{u}}$$

$$D=\left.\frac{\partial g}{\partial u}\right|_{\bar{x},\bar{u}}$$

Exam trap: The Jacobian is evaluated at the chosen equilibrium, not at the origin unless the origin is the chosen equilibrium.

---

## 4. Discrete-Time Modelling

### Why Discrete Models Matter

Digital controllers operate on sampled data. The continuous plant may be physical, but the controller computes inputs at discrete times:

$$t=kT$$

where $T$ is the sample period and $f_s=1/T$ is the sample frequency.

### Exact Discrete-Time State Space Under ZOH

For continuous-time LTI dynamics:

$$\dot{x}=Ax+Bu$$

with zero-order hold input over each sample interval:

$$u(kT+\tau)=u(kT),\quad 0\leq\tau<T$$

the exact sampled model is:

$$x(kT+T)=Gx(kT)+Hu(kT)$$

$$y(kT)=Cx(kT)+Du(kT)$$

where:

$$G=e^{AT}$$

$$H=\int_0^T e^{A\lambda}d\lambda B$$

If $A$ is invertible:

$$H=A^{-1}(G-I)B=A^{-1}(e^{AT}-I)B$$

If $A$ is singular, use the integral directly, Laplace methods, or the series:

$$H=\left(IT+\frac{AT^2}{2}+\frac{A^2T^3}{6}+\cdots\right)B$$

Key point: The exact ZOH discrete model is exact at the sampling instants, not necessarily between samples.

### Euler Forward Approximation

Using

$$\dot{x}(kT)\approx\frac{x(kT+T)-x(kT)}{T}$$

gives:

$$x(kT+T)\approx x(kT)+Tf(x(kT),u(kT))$$

For LTI systems:

$$G\approx I+AT$$

$$H\approx BT$$

This is only an approximation and requires sufficiently small $T$.

---

## 5. Sampling, Z Transform, And Discrete Stability

### Z Transform

For a sampled signal:

$$x^*(t)=\sum_{k=0}^{\infty}x[k]\delta(t-kT)$$

the unilateral z-transform is:

$$X(z)=\sum_{k=0}^{\infty}x[k]z^{-k}$$

Connection to Laplace:

$$z=e^{sT}$$

$$s=\frac{1}{T}\ln(z)$$

### s-Plane To z-Plane Mapping

| Continuous Pole Location | Discrete Pole Location |
|---|---|
| $\Re(s)<0$ | $\lvert z\rvert<1$ |
| $\Re(s)=0$ | $\lvert z\rvert=1$ |
| $\Re(s)>0$ | $\lvert z\rvert>1$ |

Frequency wrapping occurs because the imaginary axis maps repeatedly around the unit circle.

### Discrete-Time Stability

For a discrete-time transfer function or state-space model:

$$x(k+1)=Gx(k)+Hu(k)$$

asymptotic stability requires every pole/eigenvalue to satisfy:

$$|z_i|<1$$

State-space characteristic equation:

$$\det(zI-G)=0$$

Closed-loop transfer-function characteristic equation:

$$1+F(z)H(z)=0$$

### Sampling Time Selection

Rules of thumb from the notes:

$$f_s>2f$$

for Nyquist reconstruction of a signal with highest frequency $f$.

For practical control:

$$f_s\geq10f$$

and often:

$$f_s\approx20f\text{ to }40f$$

Trade-off:

- Sampling too slowly causes aliasing, poor tracking, and poor disturbance rejection.
- Sampling too quickly increases computational load, sensor noise sensitivity, and implementation cost.
- Practical goal: sample as slowly as performance allows.

### Aliasing

Aliasing occurs when high-frequency content is sampled too slowly and appears as lower-frequency content. In control systems this can cause the controller to respond to misinterpreted noise or unmodelled dynamics.

---

## 6. Digital State Feedback Design

### Discrete State Feedback

Plant:

$$x(k+1)=Gx(k)+Hu(k)$$

State feedback law for regulation:

$$u(k)=-Kx(k)$$

Closed-loop dynamics:

$$x(k+1)=(G-HK)x(k)$$

The gain $K$ is selected so that eigenvalues of $G-HK$ are in desired locations inside the unit circle.

### Controllability

The controllability matrix is:

$$\mathcal{C}_{GH}=\begin{bmatrix}H & GH & G^2H & \cdots & G^{n-1}H\end{bmatrix}$$

The system is completely state controllable iff:

$$\operatorname{rank}(\mathcal{C}_{GH})=n$$

For square controllability matrices, full rank is equivalent to:

$$\det(\mathcal{C}_{GH})\neq0$$

If the system is not controllable, not all closed-loop poles can be assigned. Uncontrollable modes may still be acceptable if already stable.

### Observability

The observability matrix is:

$$\mathcal{O}_{GC}=\begin{bmatrix}C \\ CG \\ CG^2 \\ \vdots \\ CG^{n-1}\end{bmatrix}$$

The system is completely observable iff:

$$\operatorname{rank}(\mathcal{O}_{GC})=n$$

Observability means the initial state can be uniquely reconstructed from known inputs and measured outputs over a finite number of samples.

### Pole Placement Workflow

1. Check controllability of $(G,H)$.
2. Choose desired closed-loop poles $z_1,\ldots,z_n$ inside the unit circle.
3. If poles are given in the $s$-plane, map them using $z=e^{sT}$.
4. Form desired characteristic polynomial:

$$\prod_{i=1}^{n}(z-z_i)=0$$

5. Find $K$ so that:

$$\det(zI-(G-HK))$$

matches the desired polynomial.
6. Verify pole locations, transient response, steady-state error, and control effort.

### Reference Tracking With Feedforward Gain

For fixed non-zero reference tracking:

$$u(k)=K_rr(k)-Kx(k)$$

The closed-loop model is:

$$x(k+1)=(G-HK)x(k)+HK_rr(k)$$

A practical gain selection uses the final-value idea:

$$K_r=\frac{K_s}{F_{sf}(1)}$$

where $K_s$ is desired steady-state gain and $F_{sf}(1)$ is the discrete closed-loop gain at $z=1$ without feedforward correction.

Key point: $K$ sets transients and closed-loop poles. $K_r$ fixes constant-reference steady-state scaling.

---

## 7. Tracking, Disturbance Rejection, And Integral Action

### Tracking Versus Regulation

| Task | Goal |
|---|---|
| Regulation | Drive state/output to zero or an operating point |
| Tracking | Make output follow a non-zero reference |
| Disturbance rejection | Reduce or eliminate effect of disturbances |

### Internal Model Principle

To asymptotically track a reference or reject a disturbance, the controller must include the dynamics that generate that signal.

Common internal models:

| Signal | Internal Model |
|---|---|
| Step/constant | One integrator, $1/(z-1)$ |
| Ramp | Double-integrator-type model, $1/(z-1)^2$ |
| Sinusoid | Discrete oscillator |

### Integral Action Augmentation

For plant:

$$x(k+1)=Gx(k)+Hu(k)$$

$$y(k)=Cx(k)$$

add an integral state:

$$q(k+1)=q(k)+y(k)=q(k)+Cx(k)$$

Augmented state:

$$z(k)=\begin{bmatrix}x(k)\\q(k)\end{bmatrix}$$

Augmented system:

$$z(k+1)=\underbrace{\begin{bmatrix}G & 0 \\ C & I\end{bmatrix}}_{G_z}z(k)+\underbrace{\begin{bmatrix}H \\ 0\end{bmatrix}}_{H_z}u(k)$$

Output:

$$y(k)=\begin{bmatrix}C & 0\end{bmatrix}z(k)$$

Control law:

$$u(k)=-K_zz(k)=-K_xx(k)-K_Iq(k)$$

Design flow:

1. Build $G_z$ and $H_z$.
2. Check controllability of $(G_z,H_z)$.
3. Choose augmented closed-loop poles.
4. Solve for $K_z$.
5. Split $K_z$ into $K_x$ and $K_I$.

### Dynamic Extensions For Common References

Step reference:

$$q(k+1)=q(k)+e(k)$$

Ramp reference:

$$q_1(k+1)=q_1(k)+e(k)$$

$$q_2(k+1)=q_2(k)+q_1(k)$$

Sinusoidal reference:

$$q_1(k+1)=q_2(k)$$

$$q_2(k+1)=-q_1(k)+2\cos(\omega)q_2(k)+e(k)$$

---

## 8. Discrete Linear Quadratic Regulator (DLQR)

### Problem Statement

DLQR finds the optimal state-feedback control law:

$$u(k)=-Kx(k)$$

that minimises the infinite-horizon quadratic cost:

$$J=\sum_{k=0}^{\infty}\left(x(k)^TQx(k)+u(k)^TRu(k)\right)$$

with:

$$Q\succeq0$$

$$R\succ0$$

### DARE And Gain

The discrete algebraic Riccati equation is:

$$P=G^TPG-(G^TPH)(R+H^TPH)^{-1}(H^TPG)+Q$$

The optimal gain is:

$$K=(R+H^TPH)^{-1}H^TPG$$

Closed-loop system:

$$x(k+1)=(G-HK)x(k)$$

### DLQR Design Workflow

1. Check controllability of $(G,H)$.
2. Choose $Q\succeq0$ and $R\succ0$.
3. Solve the DARE for $P$.
4. Compute $K$.
5. Verify $|\lambda_i(G-HK)|<1$.
6. Simulate state response and control signal.
7. Retune $Q$ and $R$ if response or effort is unacceptable.

### DLQR Stability Conditions

Let:

$$Q=V^TV$$

If:

$$\text{the pair }(G,H)\text{ is controllable}$$

and:

$$\text{the pair }(G,V)\text{ is observable}$$

then a unique stabilising $P=P^T\succeq0$ exists and all eigenvalues of $G-HK$ lie inside the unit circle.

Important distinction: $(G,V)$ observability is about what the cost function penalises, not what sensors measure. It is not the same as $(G,C)$ observability.

### Tuning $Q$ And $R$

| Change | Typical Effect |
|---|---|
| Increase $Q$ relative to $R$ | Faster state convergence, more control effort |
| Increase $R$ relative to $Q$ | Less control effort, slower convergence |
| Increase one $q_{ii}$ | Penalise state $x_i$ more heavily |
| Increase one $r_{jj}$ | Penalise input $u_j$ more heavily |

Only the relative scaling of $Q$ and $R$ matters. Scaling both by the same positive factor generally gives the same $K$.

Bryson's rule:

$$q_{ii}\approx\left(\frac{1}{\text{max acceptable }x_i}\right)^2$$

$$r_{jj}\approx\left(\frac{1}{\text{max acceptable }u_j}\right)^2$$

Practical tuning:

- If states settle too slowly, increase relevant $Q$ entries.
- If control saturates or is too aggressive, increase relevant $R$ entries.
- Start with diagonal $Q$ and $R$ unless cross-coupling penalties have a physical reason.

### LQR Limitations

- Does not explicitly handle actuator saturation.
- Guarantees can fail if the implemented input is clipped.
- Depends on model accuracy.
- Provides implicit pole placement rather than direct pole choice.
- If constraints dominate behaviour, MPC is usually more appropriate.

---

## 9. Model Predictive Control (MPC)

### Core Idea

MPC solves a finite-horizon optimisation at each sample time, applies the first input, then re-solves at the next sample. This is the receding horizon principle.

At time $k$, solve:

$$\min_{u(k),\ldots,u(k+N-1)}\sum_{j=0}^{N-1}\left(x(k+j)^TQx(k+j)+u(k+j)^TRu(k+j)\right)$$

subject to:

$$x(k+j+1)=Gx(k+j)+Hu(k+j)$$

and constraints such as:

$$u_{min}\leq u(k+j)\leq u_{max}$$

$$x_{min}\leq x(k+j)\leq x_{max}$$

Only $u(k)$ is applied.

### LQR Versus MPC

| Feature | LQR | MPC |
|---|---|---|
| Horizon | Infinite | Finite prediction horizon |
| Online computation | Low, just $u=-Kx$ | Higher, solve optimisation online |
| Constraints | Not explicit | Explicit input/state/rate constraints |
| Tuning | $Q$, $R$ | $Q$, $R$, horizon, constraints |
| Best use | Unconstrained regulation | Constrained or nonlinear systems |

---

## 10. Observers And State Estimation

### Why Observers Are Needed

State feedback assumes $x(k)$ is available. In practice, only outputs $y(k)$ may be measured. Observers estimate the missing states.

### Discrete-Time Luenberger Observer

Plant:

$$x(k+1)=Gx(k)+Hu(k)$$

$$y(k)=Cx(k)$$

Observer:

$$\hat{x}(k+1)=G\hat{x}(k)+Hu(k)+L(y(k)-\hat{y}(k))$$

where:

$$\hat{y}(k)=C\hat{x}(k)$$

Estimation error:

$$e(k)=x(k)-\hat{x}(k)$$

Error dynamics:

$$e(k+1)=(G-LC)e(k)$$

Choose $L$ so eigenvalues of $G-LC$ are inside the unit circle and sufficiently fast.

### Observer Pole Placement

If $(G,C)$ is completely observable, eigenvalues of $G-LC$ can be arbitrarily assigned.

Workflow:

1. Check $\operatorname{rank}(\mathcal{O}_{GC})=n$.
2. Choose stable observer poles inside the unit circle.
3. Typically choose observer poles faster than controller poles.
4. Match $\det(zI-(G-LC))$ to the desired polynomial.

Duality:

$$\text{eig}(G-LC)=\text{eig}(G^T-C^TL^T)$$

MATLAB-style command:

```matlab
L = place(G', C', p)'
```

Python-style command:

```python
L = control.place(G.T, C.T, p).T
```

### Separation Principle

For observer-based control:

$$u(k)=-K\hat{x}(k)$$

the combined dynamics can be written as:

$$\begin{bmatrix}x(k+1)\\e(k+1)\end{bmatrix}=\begin{bmatrix}G-HK & HK \\ 0 & G-LC\end{bmatrix}\begin{bmatrix}x(k)\\e(k)\end{bmatrix}$$

Because the matrix is block upper triangular, closed-loop eigenvalues are the union of:

$$\text{eig}(G-HK)$$

and:

$$\text{eig}(G-LC)$$

Therefore, design $K$ and $L$ independently.

Rule of thumb from the notes: observer poles are often chosen 5 to 10 times faster than controller poles. In discrete time, this usually means closer to the origin, but not so fast that measurement noise is badly amplified.

---

## 11. Kalman Filtering

### Stochastic Model

Kalman filtering extends observer design to noisy systems:

$$x(k+1)=Gx(k)+Hu(k)+w(k)$$

$$y(k)=Cx(k)+v(k)$$

where:

| Quantity | Meaning |
|---|---|
| $w(k)$ | Process noise |
| $Q$ | Process noise covariance |
| $v(k)$ | Measurement noise |
| $R$ | Measurement noise covariance |

### Kalman Filter Interpretation

The Kalman filter is recursive and uses a predictor-corrector structure:

- Predict the next state using the model.
- Predict output from the estimated state.
- Compare actual measurement to predicted measurement.
- Correct estimate using a gain selected from uncertainty covariances.

The Kalman gain balances:

| Relative Covariance | Behaviour |
|---|---|
| Small $Q$ relative to $R$ | Trust model more, trust noisy measurement less |
| Small $R$ relative to $Q$ | Trust measurement more, correct model more aggressively |

Compared with a Luenberger observer:

| Feature | Luenberger Observer | Kalman Filter |
|---|---|---|
| Gain choice | Pole placement | Noise-covariance optimisation |
| Noise model | Not explicit | Explicit $Q$ and $R$ |
| Gain | Usually constant | Often time-varying, may converge steady-state |
| Main trade-off | Speed versus noise amplification | Model uncertainty versus measurement uncertainty |

### Choosing $R$

For $p$ outputs, $R\in\mathbb{R}^{p\times p}$. If sensor noise is uncorrelated, use a diagonal matrix:

$$R=\operatorname{diag}(\sigma_{v_1}^2,\ldots,\sigma_{v_p}^2)$$

Sources:

- Sensor datasheets.
- Experimental measurements of sensor variance.
- Cross-covariance if sensors have correlated noise.

### Choosing $Q$

For $n$ states, $Q\in\mathbb{R}^{n\times n}$. It is often diagonal and tuned based on expected model mismatch:

$$Q=\operatorname{diag}(\sigma_{w_1}^2,\ldots,\sigma_{w_n}^2)$$

Larger entries mean you expect larger unmodelled disturbances or modelling error in those states.

### Residual Analysis

Residual:

$$e(k)=y(k)-\hat{y}^-(k)=y(k)-C\hat{x}^-(k)$$

For a well-tuned Kalman filter, residuals should be approximately:

- Zero mean.
- White, meaning uncorrelated over time.
- Consistent with expected covariance.

Residual tuning table:

| Symptom | Possible Cause | Action |
|---|---|---|
| Non-zero mean | Sensor bias or model bias | Check calibration and model |
| Strong autocorrelation | $Q/R$ mismatch or model structure issue | Retune and inspect model |
| Residual variance too high | $R$ too small or $Q$ too large | Increase $R$ or decrease $Q$ |
| Residual variance too low | $R$ too large or $Q$ too small | Decrease $R$ or increase $Q$ |

---

## 12. Practical Controller Discretisation

These methods convert a continuous controller $G_c(s)$ to a discrete controller $G_d(z)$.

### Tustin Bilinear Transform

Substitution:

$$s\leftarrow\frac{2}{T}\frac{z-1}{z+1}$$

so:

$$G_d(z)=G_c\left(\frac{2}{T}\frac{z-1}{z+1}\right)$$

Properties:

- Maps the continuous left-half plane into the unit circle.
- Maps the imaginary axis to $|z|=1$.
- Preserves stability.
- Causes frequency warping.

Implementation:

```matlab
Gd = c2d(Gc, T, 'tustin')
```

```python
Gd = signal.cont2discrete(Gc, dt=T, method='bilinear')
```

### Zero-Order Hold Equivalent

ZOH transfer function:

$$G_{zoh}(s)=\frac{1-e^{-sT}}{s}$$

Discrete pulse transfer form:

$$G_d(z)=\mathcal{Z}\left\{\mathcal{L}^{-1}\left[\frac{1-e^{-sT}}{s}G_c(s)\right]\right\}$$

Equivalent expression:

$$G_d(z)=(1-z^{-1})\mathcal{Z}\left\{\frac{G_c(s)}{s}\right\}$$

Properties:

- Exact at sampling instants for staircase input.
- Preserves stability if $G_c(s)$ is stable.
- Can introduce phase lag.

Implementation:

```matlab
Gd = c2d(Gc, T, 'zoh')
```

```python
Gd = signal.cont2discrete(Gc, dt=T, method='zoh')
```

### Matched Pole-Zero Method

Map each continuous pole and zero using:

$$z=e^{sT}$$

Form:

$$G_d(z)=K_d\frac{\prod(z-z_{z_j})}{\prod(z-z_{p_i})}$$

Then adjust $K_d$ by matching DC gain:

$$G_d(1)=G_c(0)$$

If needed, add zeros at $z=-1$ until the numerator order is equal to or one less than the denominator order.

Properties:

- Preserves mapped pole/zero locations.
- Preserves DC gain.
- Stable continuous poles map to stable discrete poles.
- Often useful when dominant pole/zero locations matter.

---

## 13. Formula Quick Reference

### Continuous And Discrete State Space

| Item | Formula |
|---|---|
| Continuous state space | $\dot{x}=Ax+Bu$, $y=Cx+Du$ |
| Transfer function | $H(s)=C(sI-A)^{-1}B+D$ |
| Continuous response | $x(t)=e^{At}x_0+\int_0^t e^{A(t-\tau)}Bu(\tau)d\tau$ |
| Exact discrete model | $x(k+1)=Gx(k)+Hu(k)$ |
| Discrete $G$ | $G=e^{AT}$ |
| Discrete $H$ | $H=\int_0^T e^{A\lambda}d\lambda B$ |
| If $A$ invertible | $H=A^{-1}(G-I)B$ |
| s-z mapping | $z=e^{sT}$ |

### Stability And Design

| Item | Formula/Test |
|---|---|
| CT internal stability | $\Re(\lambda_i(A))<0$ |
| DT stability | $\lvert\lambda_i(G)\rvert<1$ |
| Controllability | $\operatorname{rank}[H\ GH\ \cdots\ G^{n-1}H]=n$ |
| Observability | $\operatorname{rank}[C^T\ (CG)^T\ \cdots\ (CG^{n-1})^T]^T=n$ |
| State feedback | $u=-Kx$ |
| Closed-loop matrix | $G-HK$ |
| Observer error matrix | $G-LC$ |
| DLQR gain | $K=(R+H^TPH)^{-1}H^TPG$ |
| DARE | $P=G^TPG-(G^TPH)(R+H^TPH)^{-1}(H^TPG)+Q$ |

### Common Transforms

| Time Domain | Laplace Domain |
|---|---|
| $\delta(t)$ | $1$ |
| $u(t)$ | $1/s$ |
| $t$ | $1/s^2$ |
| $t^n$ | $n!/s^{n+1}$ |
| $e^{at}$ | $1/(s-a)$ |
| $\sin(\omega t)$ | $\omega/(s^2+\omega^2)$ |
| $\cos(\omega t)$ | $s/(s^2+\omega^2)$ |
| $e^{at}\sin(\omega t)$ | $\omega/((s-a)^2+\omega^2)$ |
| $e^{at}\cos(\omega t)$ | $(s-a)/((s-a)^2+\omega^2)$ |

---

## 14. Exam Problem Workflows

### A. Convert State Space To Transfer Function

1. Write $sI-A$.
2. Compute $(sI-A)^{-1}$.
3. Multiply $C(sI-A)^{-1}B+D$ in order.
4. Simplify numerator and denominator.
5. Poles come from denominator or $\det(sI-A)=0$.

### B. Analyse Continuous-Time Stability

1. If given transfer function, inspect poles for BIBO stability.
2. If given state space, compute eigenvalues of $A$ for internal stability.
3. Watch for pole-zero cancellation: BIBO stability does not always mean internal stability.
4. If asked for Lyapunov proof, set up $A^TP+PA=-Q$ with $Q\succ0$.

### C. Linearise A Nonlinear System

1. Solve $f(\bar{x},\bar{u})=0$.
2. Compute $A=\partial f/\partial x$ and $B=\partial f/\partial u$.
3. Evaluate both at $(\bar{x},\bar{u})$.
4. If output is nonlinear, compute $C=\partial g/\partial x$ and $D=\partial g/\partial u$.
5. Write incremental model in $\delta x$, $\delta u$, and $\delta y$.

### D. Discretise A Continuous State-Space Model

1. Choose sample period $T$.
2. Compute $G=e^{AT}$.
3. Compute $H=\int_0^T e^{A\lambda}d\lambda B$.
4. If $A$ is invertible, use $H=A^{-1}(G-I)B$.
5. Keep $C$ and $D$ unchanged for sampled output model.

### E. Design Discrete Pole Placement Controller

1. Check controllability rank.
2. Choose desired $z$-plane poles.
3. Convert desired $s$ poles using $z=e^{sT}$ if needed.
4. Form desired characteristic polynomial.
5. Solve for $K$ from $\det(zI-(G-HK))$.
6. Verify $|z_i|<1$ and simulate response.

### F. Add Integral Action

1. Decide what signal must be integrated, usually tracking error or output deviation.
2. Add integrator state $q(k+1)=q(k)+e(k)$ or $q(k+1)=q(k)+y(k)$ depending on formulation.
3. Build augmented matrices.
4. Check augmented controllability.
5. Design $K_z=[K_x\ K_I]$.
6. Verify steady-state error goes to zero for the intended signal class.

### G. Design DLQR

1. Confirm $(G,H)$ controllable.
2. Choose diagonal $Q$ and $R$ to start.
3. Use Bryson's rule if maximum acceptable state/input magnitudes are known.
4. Solve DARE.
5. Compute $K$.
6. Check eigenvalues of $G-HK$.
7. Simulate state and input responses.
8. Retune: more $Q$ for faster states, more $R$ for lower effort.

### H. Design Observer

1. Check observability of $(G,C)$.
2. Choose observer poles inside unit circle.
3. Place them faster than controller poles, but avoid excessive noise amplification.
4. Compute $L$ using dual pole placement.
5. Verify error dynamics $G-LC$ are stable.

### I. Tune Kalman Filter

1. Estimate $R$ from sensor data or datasheets.
2. Choose initial $Q$ from physical model uncertainty.
3. Run the filter and collect residuals.
4. Check residual mean, variance, and autocorrelation.
5. Adjust $Q$ and $R$ until residuals are approximately zero-mean and white.

---

## 15. Common Exam Traps

- Confusing continuous-time stability with discrete-time stability. CT stable means $\Re(s)<0$; DT stable means $|z|<1$.
- Forgetting to map desired continuous poles to discrete poles using $z=e^{sT}$ before discrete pole placement.
- Treating $G$ and $H$ as transfer functions when they are discrete state-space matrices.
- Using $H=A^{-1}(G-I)B$ when $A$ is singular.
- Forgetting that $C$ and $D$ usually remain unchanged in exact sampled state-space models.
- Checking observability with $C$ when the DLQR theorem asks for observability of $(G,V)$ where $Q=V^TV$.
- Assuming LQR handles saturation. It does not explicitly handle constraints.
- Placing observer poles extremely fast and then amplifying measurement noise.
- Assuming BIBO stability implies internal stability even when pole-zero cancellations may hide unstable modes.
- Linearising around the origin when the equilibrium is not the origin.
- Forgetting that integral action changes system order and requires checking augmented controllability.
- Confusing process noise covariance $Q$ in Kalman filtering with state penalty $Q$ in LQR. Same symbol, different meaning.

---

## 16. Quick Concept Checks

1. If $A$ has an eigenvalue at $+2$, the continuous autonomous system is internally unstable.
2. If $G$ has an eigenvalue $1.05$, the discrete autonomous system is unstable.
3. If $\operatorname{rank}(\mathcal{C}_{GH})<n$, arbitrary pole placement is not possible.
4. If $\operatorname{rank}(\mathcal{O}_{GC})<n$, a full-order observer cannot arbitrarily place all observer poles.
5. If $Q$ is increased relative to $R$ in DLQR, expect faster response and larger control effort.
6. If $R$ is increased relative to $Q$ in DLQR, expect slower response and smaller control effort.
7. For step disturbance rejection, include an integrator in the controller.
8. For sinusoidal tracking, include oscillator dynamics corresponding to the sinusoid.
9. In Kalman filtering, large measurement noise covariance makes the estimator trust the model more.
10. In Tustin discretisation, the stable continuous left-half plane maps inside the unit circle.

---

## 17. Minimal MATLAB/Python Command Memory

MATLAB:

```matlab
G = expm(A*T);
H = inv(A)*(G-eye(size(A)))*B;   % only if A is invertible
[G,H] = c2d(A,B,T);
K = place(G,H,poles);
L = place(G',C',observer_poles)';
Gd = c2d(Gc,T,'zoh');
Gd = c2d(Gc,T,'tustin');
Gd = c2d(Gc,T,'matched');
```

Python-style:

```python
from scipy.linalg import expm, solve_discrete_are
from scipy import signal
import control

G = expm(A*T)
P = solve_discrete_are(G, H, Q, R)
K = np.linalg.inv(R + H.T @ P @ H) @ (H.T @ P @ G)
L = control.place(G.T, C.T, observer_poles).T
Gd = signal.cont2discrete(system, dt=T, method='zoh')
Gd_tustin = signal.cont2discrete(system, dt=T, method='bilinear')
```
