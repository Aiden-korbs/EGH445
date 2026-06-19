# EGH445 Exam Resource Sheet - 2 Page

## Page 1 - Modelling, Analysis, Discretisation

### State-Space Essentials

| Item | Continuous time | Discrete time |
|---|---|---|
| Model | $\dot{x}=Ax+Bu$, $y=Cx+Du$ | $x(k+1)=Gx(k)+Hu(k)$, $y(k)=Cx(k)+Du(k)$ |
| Dimensions | $A:n\times n$, $B:n\times m$, $C:p\times n$, $D:p\times m$ | $G:n\times n$, $H:n\times m$, $C:p\times n$, $D:p\times m$ |
| TF | $G(s)=C(sI-A)^{-1}B+D$ | $G(z)=C(zI-G)^{-1}H+D$ |
| Poles | $\det(sI-A)=0$ | $\det(zI-G)=0$ |
| Stability | all $\operatorname{Re}(\lambda(A))<0$ | all $|\lambda(G)|<1$ |

State = minimum information needed to predict future behaviour for known input. Internal stability checks all state modes; BIBO stability checks input-output poles only. Pole-zero cancellation can hide internally unstable modes. Block rules: series $G_1G_2$, parallel $G_1+G_2$, negative feedback $G_1/(1+G_1G_2)$, positive feedback $G_1/(1-G_1G_2)$.

**Response formulas:** $x(t)=e^{At}x_0+\int_0^t e^{A(t-\tau)}Bu(\tau)d\tau$. If $A=T\Lambda T^{-1}$, $e^{At}=Te^{\Lambda t}T^{-1}$. Lyapunov CT test: solve $A^TP+PA=-Q$; if $Q\succ0$ and $P\succ0$, asymptotically stable.

**Eigenvalue response memory:** real negative = exponential decay; real positive = exponential growth; complex pair = oscillation; negative real complex = decaying oscillation; positive real complex = growing oscillation; zero or pure imaginary = marginal/integrator behaviour. DT poles near origin = fast decay; poles near unit circle = slow decay/oscillation; negative DT pole = alternating sign.

**2x2 inverse shortcut:** if $M=\begin{bmatrix}a&b\\c&d\end{bmatrix}$, then $M^{-1}=\frac{1}{ad-bc}\begin{bmatrix}d&-b\\-c&a\end{bmatrix}$. Useful for $C(sI-A)^{-1}B$ and $C(zI-G)^{-1}H$.

**Mini example - TF/stability:** $A=\begin{bmatrix}0&1\\-2&-3\end{bmatrix}$, $B=\begin{bmatrix}0\\1\end{bmatrix}$, $C=[1\ 0]$. $\det(sI-A)=s^2+3s+2=(s+1)(s+2)$, so poles $-1,-2$ and stable. $G(s)=1/(s^2+3s+2)$.

### Linearisation Workflow

For $\dot{x}=f(x,u)$, $y=g(x,u)$:

1. Find equilibrium: $0=f(\bar{x},\bar{u})$, $\bar{y}=g(\bar{x},\bar{u})$.
2. Define increments: $\delta x=x-\bar{x}$, $\delta u=u-\bar{u}$, $\delta y=y-\bar{y}$.
3. Compute Jacobians at the chosen equilibrium:

$$
A=\left.\frac{\partial f}{\partial x}\right|_{\bar{x},\bar{u}},\quad B=\left.\frac{\partial f}{\partial u}\right|_{\bar{x},\bar{u}},\quad C=\left.\frac{\partial g}{\partial x}\right|_{\bar{x},\bar{u}},\quad D=\left.\frac{\partial g}{\partial u}\right|_{\bar{x},\bar{u}}
$$

4. Write $\delta\dot{x}=A\delta x+B\delta u$, $\delta y=C\delta x+D\delta u$.

**Traps:** do not linearise at the origin unless it is the specified equilibrium; linearisation is local; different equilibria can produce different stability. Linearity test: additivity and homogeneity.

**Mini examples:** If $\dot{x}=x^2+u$, $y=x$, $\bar{x}=2$, then $\bar{u}=-4$, $A=2\bar{x}=4$, $B=1$, $C=1$, $D=0$. If $\dot{x}_2=-(g/l)\sin x_1+u$, then $\partial\dot{x}_2/\partial x_1=-(g/l)\cos\bar{x}_1$; at $0$ gives $-g/l$, at $\pi$ gives $+g/l$.

**Mechanical modelling pattern:** choose states as position and velocity. For $m\ddot{y}+b\dot{y}+ky=u$, let $x_1=y$, $x_2=\dot{y}$, so $\dot{x}_1=x_2$, $\dot{x}_2=-(k/m)x_1-(b/m)x_2+(1/m)u$, $y=[1\ 0]x$. For electrical RC: state often capacitor voltage; use KCL and component laws to isolate $\dot{x}$.

### Discrete Modelling, Sampling, Z-Plane

Exact ZOH discretisation for $\dot{x}=Ax+Bu$:

$$
G=e^{AT},\qquad H=\int_0^T e^{A\lambda}B\,d\lambda,\qquad y(k)=Cx(k)+Du(k)
$$

If $A$ invertible: $H=A^{-1}(G-I)B$. If $A$ singular: use integral, augmented matrix exponential, Laplace method, or series $H=(IT+AT^2/2+A^2T^3/6+\cdots)B$. Euler approximation: $G\approx I+AT$, $H\approx BT$ only for small $T$.

**Mapping:** $z=e^{sT}$, $s=(1/T)\ln z$. CT LHP maps inside unit circle; imaginary axis maps to unit circle; RHP maps outside. For $s=\sigma\pm j\omega$, $z=e^{\sigma T}e^{\pm j\omega T}$, so radius $e^{\sigma T}$ and angle $\omega T$.

**Sampling:** $T=1/f_s$. Nyquist: $f_s>2f_{max}$. Practical control: usually $f_s\ge10f_{bw}$, often $20$ to $40$ times bandwidth. Too slow = aliasing, delay, poor tracking/rejection. Too fast = noise sensitivity, computation/hardware cost.

**Mini examples:** $\dot{x}=-2x+u$, $T=0.1$: $G=e^{-0.2}=0.8187$, $H=(-1/2)(0.8187-1)=0.0906$. Pole $s=-4$, $T=0.1$: $z=e^{-0.4}=0.6703$. Poles $s=-2\pm j5$, $T=0.1$: radius $0.8187$, angle $\pm0.5$ rad.

**Difference equation to pulse TF:** apply $\mathcal Z\{y[k-i]\}=z^{-i}Y(z)$ assuming zero initial conditions. Example: $y[k]-0.5y[k-1]=2u[k-1]$ gives $Y(z)(1-0.5z^{-1})=2z^{-1}U(z)$, so $G(z)=Y/U=2z^{-1}/(1-0.5z^{-1})=2/(z-0.5)$.

**Common z-transform facts:** delay by one sample multiplies by $z^{-1}$; poles inside unit circle decay; pole at $z=1$ is an integrator/step-memory mode; pole at $z=-1$ gives alternating marginal oscillation.

### Controllability, Observability, Final Value

| Test | Matrix | Condition | Meaning |
|---|---|---|---|
| DT controllability | $\mathcal C=[H\ GH\ \cdots\ G^{n-1}H]$ | $\operatorname{rank}(\mathcal C)=n$ | input can move all modes |
| DT observability | $\mathcal O=\begin{bmatrix}C\\CG\\\vdots\\CG^{n-1}\end{bmatrix}$ | $\operatorname{rank}(\mathcal O)=n$ | outputs reveal all modes |
| CT versions | replace $(G,H,C)$ with $(A,B,C)$ | same rank tests | continuous models |

If square, non-zero determinant implies full rank. Use controllability for state-feedback design; use observability for observer design. Discrete final value theorem: if stable, $\lim_{k\to\infty}y[k]=\lim_{z\to1}(1-z^{-1})Y(z)$.

**Mini example - controllability:** $G=\begin{bmatrix}1&1\\0&1\end{bmatrix}$, $H=\begin{bmatrix}0\\1\end{bmatrix}$. $GH=\begin{bmatrix}1\\1\end{bmatrix}$, so $\mathcal C=\begin{bmatrix}0&1\\1&1\end{bmatrix}$, $\det=-1\ne0$: controllable.

**Observability mini example:** for $G=\begin{bmatrix}1&0.1\\0&0.9\end{bmatrix}$ and $C=[1\ 0]$, $CG=[1\ 0.1]$, so $\mathcal O=\begin{bmatrix}1&0\\1&0.1\end{bmatrix}$ has determinant $0.1\ne0$: observable. If $C=[0\ 1]$, then $CG=[0\ 0.9]$ and rank is one: not observable.

**Exam conclusion wording:** after a rank/eigenvalue test, write the condition and conclusion in words. Example: $\operatorname{rank}(\mathcal C)=2=n$, therefore all modes are controllable and arbitrary DT pole placement is possible.

\pagebreak

## Page 2 - Control Design, Estimation, Practical Methods

### State Feedback, Tracking, Integral Action

State feedback: $u(k)=-Kx(k)$, closed-loop matrix $G_{cl}=G-HK$. Closed-loop poles are $\operatorname{eig}(G-HK)$. Pole placement workflow: check controllability; choose DT poles inside unit circle; convert CT poles with $z=e^{sT}$ if needed; match $\det(zI-(G-HK))$ to desired polynomial; verify response and control effort.

**Pole placement template:** for $G=\begin{bmatrix}1&1\\0&1\end{bmatrix}$, $H=\begin{bmatrix}0\\1\end{bmatrix}$, $K=[k_1\ k_2]$, $G-HK=\begin{bmatrix}1&1\\-k_1&1-k_2\end{bmatrix}$. Match $\det(zI-(G-HK))$ to $(z-z_1)(z-z_2)$.

**Pole choice guide:** poles closer to origin = faster response but larger control effort; poles closer to unit circle = slower response but lower effort; complex poles = oscillatory response; repeated poles can create sensitivity. Always check actuator saturation after placing fast poles.

Tracking vs regulation: regulation drives output/state to zero; tracking drives output to $r$. Constant-reference tracking can use $u=K_rr-Kx$. Integral action is more robust for unknown constant disturbances. Internal model principle: to track/reject a signal asymptotically, controller must include that signal's dynamics: step = one integrator; ramp = two integrators; sinusoid = oscillator.

**Reference feedforward:** for SISO $D=0$, steady-state constant tracking with $u=K_rr-Kx$ can use $K_r=1/[C(I-G+HK)^{-1}H]$ when the closed loop is stable and the inverse exists. If model mismatch/disturbance exists, prefer integral action.

Integral augmentation examples:

$$
q(k+1)=q(k)+r(k)-y(k) \quad \text{or} \quad q(k+1)=q(k)+y(k)
$$

For output-integrator convention:

$$
z=\begin{bmatrix}x\\q\end{bmatrix},\quad G_z=\begin{bmatrix}G&0\\C&I\end{bmatrix},\quad H_z=\begin{bmatrix}H\\0\end{bmatrix},\quad u=-K_z z=-K_xx-K_Iq
$$

Check augmented controllability before placing augmented poles. Integral action increases system order and can increase overshoot/control effort.

**Sinusoidal internal model:** a sinusoid with discrete frequency $\omega$ can be generated by a second-order oscillator with characteristic $z^2-2\cos(\omega)z+1$. Add oscillator states if sinusoidal tracking/rejection is required.

**Disturbance feedforward idea:** if a measurable disturbance $d$ enters through $H_d$, use a feedforward term to cancel its steady-state effect. If the disturbance is unmeasured or model is uncertain, integral action is usually more robust.

### DLQR And MPC

DLQR minimises infinite-horizon quadratic cost:

$$
J=\sum_{k=0}^{\infty}\left[x(k)^TQx(k)+u(k)^TRu(k)\right],\qquad Q\succeq0,\ R\succ0
$$

DARE and gain:

$$
P=G^TPG-(G^TPH)(R+H^TPH)^{-1}(H^TPG)+Q,\qquad K=(R+H^TPH)^{-1}H^TPG
$$

Stability theorem: if $(G,H)$ controllable and $(G,V)$ observable where $Q=V^TV$, then the stabilising solution gives stable $G-HK$. Note: $(G,V)$ is cost observability, not sensor observability $(G,C)$.

**Tuning sheet:** larger $q_{ii}$ penalises state $x_i$ more; larger $r_{jj}$ penalises input $u_j$ more. Larger $Q/R$ = faster, more aggressive, more input. Larger $R/Q$ = slower, less input. Scaling both $Q$ and $R$ by the same factor gives same $K$. Bryson rule: $q_{ii}\approx1/x_{i,max}^2$, $r_{jj}\approx1/u_{j,max}^2$. If too slow: increase relevant $Q$. If saturated/noisy input: increase $R$. LQR does not explicitly handle constraints.

MPC: finite-horizon optimisation solved online each sample; applies first input only, then re-solves. Handles input/state/rate constraints and saturation directly. More computational cost than LQR.

**MPC cost template:** minimise $\sum_{j=0}^{N-1}(x_{k+j}^TQx_{k+j}+u_{k+j}^TRu_{k+j})+x_{k+N}^TP_fx_{k+N}$ subject to $x_{k+j+1}=Gx_{k+j}+Hu_{k+j}$ and constraints. Larger horizon $N$ improves planning but increases computation.

### Observers, Output Feedback, Kalman Filters

Open-loop predictor $\hat{x}(k+1)=G\hat{x}(k)+Hu(k)$ has error $e(k+1)=Ge(k)$, so unstable or slow plants give bad estimates. Luenberger observer:

$$
\hat{x}(k+1)=G\hat{x}(k)+Hu(k)+L[y(k)-C\hat{x}(k)]
$$

Error $e=x-\hat{x}$ follows $e(k+1)=(G-LC)e(k)$. Observer design workflow: check observability of $(G,C)$; choose observer poles inside unit circle; make them faster than controller poles but not too fast; compute `L=place(G',C',poles)'`.

Output feedback: $u=-K\hat{x}$. Separation principle:

$$
\begin{bmatrix}x(k+1)\\e(k+1)\end{bmatrix}=\begin{bmatrix}G-HK&HK\\0&G-LC\end{bmatrix}\begin{bmatrix}x(k)\\e(k)\end{bmatrix}
$$

Overall poles = controller poles $\operatorname{eig}(G-HK)$ plus observer poles $\operatorname{eig}(G-LC)$. Design $K$ and $L$ independently for ideal models. Fast observer poles give fast convergence but amplify measurement noise.

Kalman model: $x(k+1)=Gx(k)+Hu(k)+w(k)$, $y(k)=Cx(k)+v(k)$. $Q=E[ww^T]$ process/model-noise covariance; $R=E[vv^T]$ measurement-noise covariance. Larger $Q/R$ = trust measurements more; estimates respond faster but noisier. Smaller $Q/R$ = trust model more; smoother but may drift or lag. Residual $r(k)=y(k)-C\hat{x}^-(k)$ should be zero-mean, white, and expected variance. Non-zero mean = bias; correlated residuals = model/tuning mismatch. EKF linearises nonlinear $f,h$ about current estimate each step; useful but approximate and more computationally expensive.

**Kalman predict-correct skeleton:** predict $\hat{x}^-=G\hat{x}+Hu$, $P^-=GPG^T+Q$; update $K_k=P^-C^T(CP^-C^T+R)^{-1}$, $\hat{x}=\hat{x}^-+K_k(y-C\hat{x}^-)$, $P=(I-K_kC)P^-$. Luenberger chooses $L$ by poles; Kalman computes gain from uncertainty.

**Observer mini example:** if controller poles are $0.7,0.8$, observer poles $0.2,0.3$ are faster. If sensor noise dominates, move observer poles less aggressively toward zero.

### Controller Discretisation By Emulation

Direct design: discretise plant, design controller in $z$ domain. Emulation: design $G_c(s)$ first, convert to $G_d(z)$.

| Method | Rule | Main use / warning |
|---|---|---|
| Tustin/bilinear | $s\leftarrow\frac{2}{T}\frac{z-1}{z+1}$ | preserves stability; frequency warping |
| ZOH equivalent | $G_d(z)=(1-z^{-1})\mathcal Z\{G_c(s)/s\}$ | exact at sample instants for staircase input; phase lag |
| Matched pole-zero | map each pole/zero with $z=e^{sT}$, match $G_d(1)=G_c(0)$ | preserves pole/zero locations; add zeros at $z=-1$ if needed |

Commands: MATLAB `expm(A*T)`, `c2d(sys,T,'zoh')`, `c2d(sys,T,'tustin')`, `c2d(sys,T,'matched')`, `place(G,H,p)`, `place(G',C',p)'`, `dlqr(G,H,Q,R)`. Python: `signal.cont2discrete`, `solve_discrete_are`, `control.place`.

**Emulation quick example:** continuous pole $s=-a$ maps by MPZ to $z=e^{-aT}$. For Tustin, substitute $s=(2/T)(z-1)/(z+1)$ directly into $G_c(s)$, then simplify and normalise powers of $z$ or $z^{-1}$.

### High-Yield Traps And Memory List

CT stability uses $\operatorname{Re}(s)<0$; DT stability uses $|z|<1$. Convert CT poles to DT poles before discrete pole placement. Do not use $H=A^{-1}(G-I)B$ if $A$ is singular. Exact ZOH usually keeps $C,D$ unchanged. Controllability is for moving states with inputs; observability is for reconstructing states from outputs. BIBO stable does not guarantee internally stable if unstable modes are hidden. Integral action changes system order and requires augmented controllability. LQR $Q$ = state penalty; Kalman $Q$ = process noise. DLQR theorem uses $(G,V)$ with $Q=V^TV$, not $(G,C)$. Standard LQR does not handle saturation; MPC does. Very fast observer poles amplify noise.

Minimum formulas to memorise: $C(sI-A)^{-1}B+D$, $G=e^{AT}$, $H=\int_0^T e^{A\lambda}B\,d\lambda$, $z=e^{sT}$, $\mathcal C=[H\ GH\ \cdots\ G^{n-1}H]$, $\mathcal O=[C;CG;\cdots;CG^{n-1}]$, $G-HK$, $G-LC$, $K=(R+H^TPH)^{-1}H^TPG$.

**Fast exam templates:** SS to TF: form $sI-A$, invert, multiply $C(\cdot)B+D$. Linearise: equilibrium, perturbations, Jacobians, incremental model. Discretise: compute $G$, compute $H$, map poles. Pole placement: controllability, target polynomial, coefficient matching. Observer: observability, target observer poles, $L=place(G',C',p)'$. LQR/Kalman concept question: define what $Q,R$ mean before describing tuning.
