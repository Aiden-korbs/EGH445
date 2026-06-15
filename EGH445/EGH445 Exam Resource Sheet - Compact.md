# EGH445 Modern Control Exam Resource Sheet - Readable Compact

Designed as a compact exam sheet: short explanations, formulas, and workflows without the long derivations from the full version.

## 1. State-Space Modelling

**General nonlinear model**

- State equation: $\dot{x}=f(x,u)$
- Output equation: $y=g(x,u)$
- Equilibrium: $0=f(\bar{x},\bar{u})$

**Continuous-time LTI model**

- $\dot{x}=Ax+Bu$, $y=Cx+Du$
- If there are $n$ states, $m$ inputs, and $p$ outputs: $A:n\times n$, $B:n\times m$, $C:p\times n$, $D:p\times m$
- State vector = minimum variables needed to determine future behaviour when input is known.

**State-space to transfer function**

- $H(s)=Y(s)/U(s)=C(sI-A)^{-1}B+D$
- Poles come from $\det(sI-A)=0$
- Matrix multiplication order matters.

**Block diagram rules**

- Series: $G_1G_2$
- Parallel: $G_1+G_2$
- Negative feedback: $G_1/(1+G_1G_2)$
- Positive feedback: $G_1/(1-G_1G_2)$

## 2. Response And Stability

**Continuous-time LTI response**

- $x(t)=e^{At}x_0+\int_0^t e^{A(t-\tau)}Bu(\tau)d\tau$
- $e^{At}=\mathcal L^{-1}\{(sI-A)^{-1}\}$
- If $A=T\Lambda T^{-1}$, then $e^{At}=Te^{\Lambda t}T^{-1}$

**Stability tests**

- CT internal/asymptotic stability: all $\Re(\lambda_i(A))<0$
- CT BIBO stability: all transfer-function poles have $\Re(s)<0$
- DT stability: all poles/eigenvalues satisfy $|z_i|<1$
- DT characteristic equation from state space: $\det(zI-G)=0$

**Important distinction**

- Internal stability is stronger than BIBO stability.
- A system may be BIBO stable but internally unstable if unstable modes are hidden by pole-zero cancellation.

**Lyapunov CT test**

- For $\dot{x}=Ax$, solve $A^TP+PA=-Q$
- If $Q=Q^T\succ0$ and $P=P^T\succ0$, the system is asymptotically stable.

**Eigenvalue memory**

- Real negative: exponential decay
- Real positive: exponential growth
- Complex with negative real part: decaying oscillation
- Complex with positive real part: growing oscillation
- Pure imaginary or zero: marginal/integrator-type behaviour

## 3. Nonlinear Systems And Linearisation

**Linearity**

- Linear systems satisfy additivity and homogeneity:
- $G(u_1+u_2)=G(u_1)+G(u_2)$
- $G(\alpha u)=\alpha G(u)$

**Linearisation workflow**

1. Find equilibrium: solve $0=f(\bar{x},\bar{u})$
2. Define increments: $\delta x=x-\bar{x}$, $\delta u=u-\bar{u}$, $\delta y=y-\bar{y}$
3. Compute Jacobians at the equilibrium:
4. $A=\left.\partial f/\partial x\right|_{\bar{x},\bar{u}}$, $B=\left.\partial f/\partial u\right|_{\bar{x},\bar{u}}$
5. $C=\left.\partial g/\partial x\right|_{\bar{x},\bar{u}}$, $D=\left.\partial g/\partial u\right|_{\bar{x},\bar{u}}$
6. Write incremental model: $\delta\dot{x}=A\delta x+B\delta u$, $\delta y=C\delta x+D\delta u$

Exam trap: evaluate at the chosen equilibrium, not automatically at the origin.

## 4. Discrete-Time Modelling And Sampling

**Exact ZOH discretisation**

- Continuous model: $\dot{x}=Ax+Bu$
- ZOH assumption: $u(kT+\tau)=u(kT)$ for $0\le\tau<T$
- Discrete model: $x(kT+T)=Gx(kT)+Hu(kT)$, $y(kT)=Cx(kT)+Du(kT)$
- $G=e^{AT}$
- $H=\int_0^T e^{A\lambda}d\lambda B$
- If $A$ invertible: $H=A^{-1}(G-I)B$
- If $A$ singular: use the integral, Laplace method, or $H=(IT+AT^2/2+A^2T^3/6+\cdots)B$

**Euler approximation**

- $\dot{x}(kT)\approx[x(kT+T)-x(kT)]/T$
- $x(k+1)\approx x(k)+Tf(x(k),u(k))$
- LTI approximation: $G\approx I+AT$, $H\approx BT$
- Use only when $T$ is sufficiently small.

**z-transform and mapping**

- $X(z)=\sum_{k=0}^{\infty}x[k]z^{-k}$
- $z=e^{sT}$, $s=(1/T)\ln z$
- CT LHP maps inside unit circle.
- CT imaginary axis maps to unit circle.
- CT RHP maps outside unit circle.

**Sampling rules**

- $T=1/f_s$
- Nyquist lower bound: $f_s>2f$
- Practical control rule: $f_s\ge10f$, often $20f$ to $40f$
- Too slow: aliasing, poor tracking, poor rejection.
- Too fast: computation cost, noise sensitivity, implementation issues.

## 5. Controllability, Observability, Pole Placement

**Controllability**

- $\mathcal C_{GH}=[H\ GH\ G^2H\ \cdots\ G^{n-1}H]$
- Completely controllable iff $\operatorname{rank}(\mathcal C_{GH})=n$
- If square, $\det(\mathcal C_{GH})\ne0$ also shows full rank.
- Meaning: inputs can move all state modes.

**Observability**

- $\mathcal O_{GC}=\begin{bmatrix}C\\CG\\CG^2\\\vdots\\CG^{n-1}\end{bmatrix}$
- Completely observable iff $\operatorname{rank}(\mathcal O_{GC})=n$
- Meaning: state can be reconstructed from output/input data over finite samples.

**State feedback**

- Control law: $u(k)=-Kx(k)$
- Closed-loop matrix: $G-HK$
- Closed-loop poles are eigenvalues of $G-HK$.

**Pole placement workflow**

1. Check controllability of $(G,H)$
2. Choose desired DT poles inside unit circle
3. If CT poles are given, convert using $z=e^{sT}$
4. Form desired polynomial $\prod_i(z-z_i)$
5. Choose $K$ so $\det(zI-(G-HK))$ matches
6. Verify poles, transient response, steady-state behaviour, and control effort

**Feedforward reference tracking**

- $u(k)=K_rr(k)-Kx(k)$
- $K$ shapes closed-loop poles/transients.
- $K_r$ corrects the constant-reference steady-state gain.
- Practical formula: $K_r=K_s/F_{sf}(1)$ for stable systems.

## 6. Tracking, Disturbance Rejection, Integral Action

**Internal model principle**

- To asymptotically track/reject a signal, the controller must contain that signal's dynamics.
- Step/constant: one integrator $1/(z-1)$
- Ramp: double-integrator-type model $1/(z-1)^2$
- Sinusoid: oscillator dynamics

**Integral augmentation**

- Plant: $x(k+1)=Gx(k)+Hu(k)$, $y(k)=Cx(k)$
- Add integrator: $q(k+1)=q(k)+y(k)$ or $q(k+1)=q(k)+e(k)$
- Augmented state: $z=[x^T\ q^T]^T$
- $G_z=\begin{bmatrix}G&0\\C&I\end{bmatrix}$, $H_z=\begin{bmatrix}H\\0\end{bmatrix}$, $C_z=[C\ 0]$
- Control: $u=-K_zz=-K_xx-K_Iq$

**Integral design workflow**

1. Choose what signal is integrated: output or tracking error
2. Build augmented model
3. Check controllability of $(G_z,H_z)$
4. Choose augmented poles
5. Solve for $K_z=[K_x\ K_I]$
6. Verify zero steady-state error for the intended signal class

**Dynamic extensions**

- Step: $q(k+1)=q(k)+e(k)$
- Ramp: $q_1(k+1)=q_1(k)+e(k)$, $q_2(k+1)=q_2(k)+q_1(k)$
- Sinusoid: $q_1(k+1)=q_2(k)$, $q_2(k+1)=-q_1(k)+2\cos(\omega)q_2(k)+e(k)$

## 7. DLQR And MPC

**DLQR problem**

- Minimise $J=\sum_{k=0}^{\infty}[x(k)^TQx(k)+u(k)^TRu(k)]$
- Conditions: $Q\succeq0$, $R\succ0$
- Control law: $u(k)=-Kx(k)$

**DARE and gain**

- $P=G^TPG-(G^TPH)(R+H^TPH)^{-1}(H^TPG)+Q$
- $K=(R+H^TPH)^{-1}H^TPG$
- Closed-loop matrix: $G-HK$

**DLQR stability theorem**

- Let $Q=V^TV$.
- If $(G,H)$ is controllable and $(G,V)$ is observable, the DARE has a unique stabilising solution and $G-HK$ is stable.
- $(G,V)$ is cost observability, not sensor observability $(G,C)$.

**DLQR tuning**

- Larger $Q/R$: faster state convergence, more control effort
- Larger $R/Q$: slower response, less control effort
- Larger $q_{ii}$: penalise state $x_i$ more
- Larger $r_{jj}$: penalise input $u_j$ more
- Bryson rule: $q_{ii}\approx(1/\max|x_i|)^2$, $r_{jj}\approx(1/\max|u_j|)^2$
- LQR does not explicitly handle saturation or constraints.

**MPC summary**

- Finite-horizon optimisation solved online at each step.
- Minimise $\sum_{j=0}^{N-1}[x(k+j)^TQx(k+j)+u(k+j)^TRu(k+j)]$
- Subject to $x(k+j+1)=Gx(k+j)+Hu(k+j)$ and constraints.
- Apply only the first input, then re-solve next sample.
- LQR: low computation, no explicit constraints.
- MPC: higher computation, handles input/state/rate constraints.

## 8. Observers And Kalman Filtering

**Luenberger observer**

- Observer: $\hat{x}(k+1)=G\hat{x}(k)+Hu(k)+L[y(k)-\hat{y}(k)]$
- Estimated output: $\hat{y}=C\hat{x}$
- Error: $e=x-\hat{x}$
- Error dynamics: $e(k+1)=(G-LC)e(k)$

**Observer design**

- Check observability of $(G,C)$.
- Choose observer poles inside unit circle.
- Common rule: observer poles 5-10 times faster than controller poles, but not so fast that sensor noise is amplified.
- Duality: $L=\operatorname{place}(G^T,C^T,p)^T$

**Separation principle**

- With $u=-K\hat{x}$:
- $\begin{bmatrix}x(k+1)\\e(k+1)\end{bmatrix}=\begin{bmatrix}G-HK&HK\\0&G-LC\end{bmatrix}\begin{bmatrix}x(k)\\e(k)\end{bmatrix}$
- Poles are the union of controller poles $\operatorname{eig}(G-HK)$ and observer poles $\operatorname{eig}(G-LC)$.
- Therefore $K$ and $L$ can be designed independently.

**Kalman filter model**

- $x(k+1)=Gx(k)+Hu(k)+w(k)$
- $y(k)=Cx(k)+v(k)$
- $Q$: process noise covariance
- $R$: measurement noise covariance
- Small $Q$ relative to $R$: trust model more
- Small $R$ relative to $Q$: trust measurements more

**Kalman tuning with residuals**

- Residual: $e(k)=y(k)-\hat{y}^-(k)=y(k)-C\hat{x}^-(k)$
- Good residuals: zero mean, white, expected variance
- Non-zero mean: sensor/model bias
- Correlated residuals: $Q/R$ mismatch or model issue
- Variance too high: $R$ too small or $Q$ too large
- Variance too low: $R$ too large or $Q$ too small

## 9. Controller Discretisation

**Tustin bilinear transform**

- Substitute $s\leftarrow\frac{2}{T}\frac{z-1}{z+1}$
- $G_d(z)=G_c\left(\frac{2}{T}\frac{z-1}{z+1}\right)$
- Preserves stability and maps CT LHP inside unit circle.
- Causes frequency warping.

**Zero-order hold equivalent**

- $G_{zoh}(s)=(1-e^{-sT})/s$
- $G_d(z)=(1-z^{-1})\mathcal Z\{G_c(s)/s\}$
- Exact at sampling instants for staircase input.
- Can introduce phase lag.

**Matched pole-zero method**

- Map each CT pole/zero with $z=e^{sT}$
- Form $G_d(z)=K_d\prod(z-z_{z_j})/\prod(z-z_{p_i})$
- Match DC gain: $G_d(1)=G_c(0)$
- Add zeros at $z=-1$ if needed to balance numerator order.

## 10. Exam Workflows And Traps

**Fast workflows**

- SS to TF: compute $C(sI-A)^{-1}B+D$
- CT stability: TF poles for BIBO, $A$ eigenvalues for internal
- Linearise: equilibrium, Jacobians, incremental model
- Discretise: compute $G=e^{AT}$ and $H=\int_0^Te^{A\lambda}d\lambda B$
- Pole placement: controllability, desired poles, characteristic matching
- DLQR: choose $Q,R$, solve DARE, compute $K$, verify $G-HK$
- Observer: observability, choose poles, compute $L$, verify $G-LC$
- Kalman: choose $Q,R$, inspect residuals, iterate

**Common traps**

- CT stability uses $\Re(s)<0$; DT stability uses $|z|<1$.
- Map CT poles to DT poles using $z=e^{sT}$ before discrete pole placement.
- Do not use $H=A^{-1}(G-I)B$ if $A$ is singular.
- $C$ and $D$ usually stay unchanged under exact sampled state-space conversion.
- DLQR theorem uses $(G,V)$ where $Q=V^TV$, not $(G,C)$.
- LQR does not handle saturation explicitly.
- Very fast observer poles can amplify measurement noise.
- BIBO stability does not guarantee internal stability if cancellations hide modes.
- Integral action changes system order and requires augmented controllability.
- Kalman $Q$ is process noise covariance; LQR $Q$ is state penalty.

## 11. Mini Reference

**Common Laplace pairs**

- $\delta(t)\leftrightarrow1$
- $1(t)\leftrightarrow1/s$
- $t\leftrightarrow1/s^2$
- $t^n\leftrightarrow n!/s^{n+1}$
- $e^{at}\leftrightarrow1/(s-a)$
- $\sin(\omega t)\leftrightarrow\omega/(s^2+\omega^2)$
- $\cos(\omega t)\leftrightarrow s/(s^2+\omega^2)$
- $e^{at}\sin(\omega t)\leftrightarrow\omega/((s-a)^2+\omega^2)$
- $e^{at}\cos(\omega t)\leftrightarrow(s-a)/((s-a)^2+\omega^2)$

**Useful commands**

- MATLAB: `G=expm(A*T)`, `[G,H]=c2d(A,B,T)`, `K=place(G,H,poles)`, `L=place(G',C',p)'`
- MATLAB: `c2d(Gc,T,'zoh')`, `c2d(Gc,T,'tustin')`, `c2d(Gc,T,'matched')`
- Python: `P=solve_discrete_are(G,H,Q,R)`
- Python: `K=inv(R+H.T@P@H)@(H.T@P@G)`
- Python: `signal.cont2discrete(system,dt=T,method='zoh'|'bilinear')`
