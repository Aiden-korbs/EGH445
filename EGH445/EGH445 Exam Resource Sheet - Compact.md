# EGH445 Modern Control Exam Resource Sheet - Compact

Print target: landscape, narrow margins, small font, 2 columns. This compact sheet keeps the same examinable coverage as the full resource sheet but removes worked explanations and duplicated spacing.

## Modelling, Response, Stability
**State space:** nonlinear $\dot{x}=f(x,u)$, $y=g(x,u)$; LTI $\dot{x}=Ax+Bu$, $y=Cx+Du$. Sizes: $A:n\times n$, $B:n\times m$, $C:p\times n$, $D:p\times m$. State = minimum variables needed to predict future given input. Transfer function: $H(s)=Y/U=C(sI-A)^{-1}B+D$; poles from $\det(sI-A)=0$; matrix order matters. Block rules: series $G_1G_2$, parallel $G_1+G_2$, negative feedback $G_1/(1+G_1G_2)$, positive feedback $G_1/(1-G_1G_2)$.

**CT response:** $x(t)=e^{At}x_0+\int_0^t e^{A(t-\tau)}Bu(\tau)d\tau$; $e^{At}=\mathcal L^{-1}\{(sI-A)^{-1}\}$; if $A=T\Lambda T^{-1}$ then $e^{At}=Te^{\Lambda t}T^{-1}$. Eigenvalue memory: real negative decays, real positive grows, complex negative real part decays oscillatory, complex positive real part grows oscillatory, imaginary axis/zero = marginal/integrator cases.

**Stability:** CT internal/asymptotic stable iff $\Re(\lambda_i(A))<0$. CT BIBO stable iff transfer-function poles have $\Re(s)<0$. Internal stability is stronger; BIBO can hide unstable internal modes via pole-zero cancellation. DT stable iff $|z_i|<1$ or $|\lambda_i(G)|<1$. DT characteristic equations: $\det(zI-G)=0$ or closed-loop $1+F(z)H(z)=0$. Lyapunov CT: for $\dot{x}=Ax$, if $A^TP+PA=-Q$ has $Q=Q^T\succ0$, $P=P^T\succ0$, system is asymptotically stable.

**Linearity/nonlinearity:** linear iff additivity $G(u_1+u_2)=G(u_1)+G(u_2)$ and homogeneity $G(\alpha u)=\alpha G(u)$. Nonlinear systems can have multiple equilibria and local, not global, stability.

**Equilibrium/linearisation:** equilibrium solves $0=f(\bar{x},\bar{u})$. Define $\delta x=x-\bar{x}$, $\delta u=u-\bar{u}$, $\delta y=y-\bar{y}$. Linear model: $\delta\dot{x}=A\delta x+B\delta u$, $\delta y=C\delta x+D\delta u$, with $A=\left.\partial f/\partial x\right|_{\bar{x},\bar{u}}$, $B=\left.\partial f/\partial u\right|_{\bar{x},\bar{u}}$, $C=\left.\partial g/\partial x\right|_{\bar{x},\bar{u}}$, $D=\left.\partial g/\partial u\right|_{\bar{x},\bar{u}}$. Evaluate Jacobians at the chosen equilibrium, not automatically at origin.

## Discrete-Time Modelling, Sampling, z-Domain
**Exact ZOH discretisation:** for $\dot{x}=Ax+Bu$ with $u(kT+\tau)=u(kT)$ for $0\le\tau<T$: $x(kT+T)=Gx(kT)+Hu(kT)$, $y(kT)=Cx(kT)+Du(kT)$, $G=e^{AT}$, $H=\int_0^T e^{A\lambda}d\lambda B$. If $A$ invertible: $H=A^{-1}(G-I)B=A^{-1}(e^{AT}-I)B$. If $A$ singular: use integral, Laplace method, or $H=(IT+AT^2/2+A^2T^3/6+\cdots)B$. Exact only at sample instants. Euler approximation: $\dot{x}(kT)\approx[x(kT+T)-x(kT)]/T$, so $x(k+1)\approx x(k)+Tf(x(k),u(k))$; LTI $G\approx I+AT$, $H\approx BT$.

**z-transform/sampling:** sampled signal $x^*(t)=\sum_{k=0}^\infty x[k]\delta(t-kT)$; unilateral $X(z)=\sum_{k=0}^\infty x[k]z^{-k}$; mapping $z=e^{sT}$, $s=(1/T)\ln z$. CT LHP maps inside unit circle; imaginary axis maps to unit circle; RHP maps outside. Frequency wrapping causes aliasing. Sampling: $T=1/f_s$; Nyquist $f_s>2f$; practical control $f_s\ge10f$, often $20f$ to $40f$. Sample too slow: aliasing/poor tracking/rejection; too fast: cost, computation, noise sensitivity. Aim: as slow as performance allows.

**Discrete final-value use:** evaluate stable DT transfer functions at $z=1$ for constant-reference steady-state gain checks.

## Controllability, Observability, State Feedback
**Controllability:** $\mathcal C_{GH}=[H\ GH\ G^2H\ \cdots\ G^{n-1}H]$; completely controllable iff $\operatorname{rank}(\mathcal C_{GH})=n$; if square, $\det(\mathcal C_{GH})\ne0$. Meaning: inputs can move all state modes. If not controllable, arbitrary pole placement impossible; uncontrollable modes may be acceptable only if stable.

**Observability:** $\mathcal O_{GC}=\begin{bmatrix}C\\CG\\CG^2\\\vdots\\CG^{n-1}\end{bmatrix}$; completely observable iff $\operatorname{rank}(\mathcal O_{GC})=n$. Meaning: initial state can be reconstructed from finite output/input data. If unobservable, estimator cannot infer all modes.

**State feedback:** plant $x(k+1)=Gx(k)+Hu(k)$; regulation law $u(k)=-Kx(k)$; closed-loop $x(k+1)=(G-HK)x(k)$. Pole placement workflow: check controllability; choose desired $z_i$ inside unit circle; if CT poles given, map $z_i=e^{s_iT}$; form $\prod_i(z-z_i)$; choose $K$ so $\det(zI-(G-HK))$ matches; verify poles, step/IC response, steady-state, control effort.

**Reference feedforward:** $u(k)=K_rr(k)-Kx(k)$; $x(k+1)=(G-HK)x(k)+HK_rr(k)$; choose $K_r=K_s/F_{sf}(1)$ when matching desired steady-state gain. $K$ shapes transients; $K_r$ corrects constant-reference gain only.

## Tracking, Disturbance Rejection, Integral Action
**Tasks:** regulation drives to zero/operating point; tracking follows non-zero reference; disturbance rejection suppresses disturbances. Internal model principle: controller must contain dynamics generating the reference/disturbance. Step/constant uses integrator $1/(z-1)$; ramp uses double-integrator-type $1/(z-1)^2$; sinusoid uses oscillator dynamics.

**Integral augmentation:** plant $x(k+1)=Gx(k)+Hu(k)$, $y(k)=Cx(k)$. Add $q(k+1)=q(k)+y(k)$ or error form $q(k+1)=q(k)+e(k)$. Augmented state $z=[x^T\ q^T]^T$; $G_z=\begin{bmatrix}G&0\\C&I\end{bmatrix}$, $H_z=\begin{bmatrix}H\\0\end{bmatrix}$, $C_z=[C\ 0]$, $u(k)=-K_zz(k)=-K_xx(k)-K_Iq(k)$. Design: build augmented matrices, check controllability, choose augmented poles, solve $K_z$, split into $K_x,K_I$.

**Dynamic extensions:** step $q(k+1)=q(k)+e(k)$; ramp $q_1(k+1)=q_1(k)+e(k)$, $q_2(k+1)=q_2(k)+q_1(k)$; sinusoid $q_1(k+1)=q_2(k)$, $q_2(k+1)=-q_1(k)+2\cos(\omega)q_2(k)+e(k)$.

## Optimal Control, MPC
**DLQR:** minimise $J=\sum_{k=0}^\infty[x(k)^TQx(k)+u(k)^TRu(k)]$, with $Q\succeq0$, $R\succ0$, using $u(k)=-Kx(k)$. DARE: $P=G^TPG-(G^TPH)(R+H^TPH)^{-1}(H^TPG)+Q$. Gain: $K=(R+H^TPH)^{-1}H^TPG$. Closed-loop: $G-HK$. Workflow: check $(G,H)$ controllable; choose $Q,R$; solve DARE for $P$; compute $K$; verify $|\lambda_i(G-HK)|<1$; simulate state/input; retune.

**DLQR stability theorem:** let $Q=V^TV$. If $(G,H)$ controllable and $(G,V)$ observable, a unique stabilising $P=P^T\succeq0$ exists and $G-HK$ is stable. $(G,V)$ observability is cost observability, not sensor observability $(G,C)$.

**DLQR tuning:** larger $Q/R$ gives faster convergence and higher control effort; larger $R/Q$ gives slower response and lower effort. Larger $q_{ii}$ penalises state $x_i$; larger $r_{jj}$ penalises input $u_j$. Relative scale matters; scaling both $Q,R$ by same positive factor usually leaves $K$ unchanged. Bryson: $q_{ii}\approx(1/\max|x_i|)^2$, $r_{jj}\approx(1/\max|u_j|)^2$. Start diagonal unless cross-penalties have a physical reason. LQR limitations: no explicit saturation/constraints, model-dependent, implicit pole placement, guarantees break under clipping; use MPC if constraints dominate.

**MPC:** finite-horizon online optimisation with receding horizon. At time $k$: minimise $\sum_{j=0}^{N-1}[x(k+j)^TQx(k+j)+u(k+j)^TRu(k+j)]$ subject to $x(k+j+1)=Gx(k+j)+Hu(k+j)$, $u_{min}\le u\le u_{max}$, optional $x_{min}\le x\le x_{max}$; apply only $u(k)$ and re-solve next sample. LQR: infinite horizon/offline/no explicit constraints/low computation. MPC: finite horizon/online optimisation/explicit constraints/higher computation.

## Observers, Output Feedback, Kalman Filtering
**Luenberger observer:** plant $x(k+1)=Gx(k)+Hu(k)$, $y(k)=Cx(k)$. Observer $\hat{x}(k+1)=G\hat{x}(k)+Hu(k)+L[y(k)-\hat{y}(k)]$, $\hat{y}=C\hat{x}$. Error $e=x-\hat{x}$ obeys $e(k+1)=(G-LC)e(k)$. If $(G,C)$ observable, place eigenvalues of $G-LC$ arbitrarily inside unit circle. Use duality: $L=\operatorname{place}(G^T,C^T,p)^T$. Observer poles commonly 5-10 times faster than controller poles, i.e. closer to origin in DT, but too fast amplifies measurement noise.

**Separation principle:** with $u=-K\hat{x}$, $\begin{bmatrix}x(k+1)\\e(k+1)\end{bmatrix}=\begin{bmatrix}G-HK&HK\\0&G-LC\end{bmatrix}\begin{bmatrix}x(k)\\e(k)\end{bmatrix}$. Eigenvalues are union of controller poles $\operatorname{eig}(G-HK)$ and observer poles $\operatorname{eig}(G-LC)$. Design $K$ and $L$ independently; certainty equivalence uses $\hat{x}$ as if it were $x$.

**Kalman filter model:** $x(k+1)=Gx(k)+Hu(k)+w(k)$, $y(k)=Cx(k)+v(k)$; process noise $w$ covariance $Q$, measurement noise $v$ covariance $R$. Recursive predictor-corrector; gain balances model vs measurement. Small process $Q$ relative to measurement $R$: trust model more. Small $R$ relative to $Q$: trust measurement more. Luenberger: pole-placement gain/no explicit noise. Kalman: noise-aware gain minimising covariance.

**KF tuning:** $R\in\mathbb R^{p\times p}$ from datasheets/experiments; if uncorrelated sensors, $R=\operatorname{diag}(\sigma_{v_i}^2)$. $Q\in\mathbb R^{n\times n}$ from physical model uncertainty/tuning; often $Q=\operatorname{diag}(\sigma_{w_i}^2)$. Residual $e(k)=y(k)-\hat{y}^-(k)=y(k)-C\hat{x}^-(k)$ should be zero-mean, white, expected covariance. Non-zero mean: bias/model error. Correlated residuals: $Q/R$ mismatch/model issue. Variance too high: $R$ too small or $Q$ too large; increase $R$ or decrease $Q$. Variance too low: $R$ too large or $Q$ too small; decrease $R$ or increase $Q$.

## Practical Controller Discretisation
**Tustin bilinear:** substitute $s\leftarrow\frac{2}{T}\frac{z-1}{z+1}$, so $G_d(z)=G_c(\frac{2}{T}\frac{z-1}{z+1})$. Preserves stability; maps CT LHP into unit circle and $j\omega$ axis to $|z|=1$; causes frequency warping. MATLAB: `c2d(Gc,T,'tustin')`. Python: `signal.cont2discrete(system,dt=T,method='bilinear')`.

**ZOH equivalent:** $G_{zoh}(s)=(1-e^{-sT})/s$; $G_d(z)=\mathcal Z\{\mathcal L^{-1}[(1-e^{-sT})G_c(s)/s]\}=(1-z^{-1})\mathcal Z\{G_c(s)/s\}$. Exact at sample instants for staircase input; preserves stability for stable $G_c$; can add phase lag. MATLAB: `c2d(Gc,T,'zoh')`. Python: `signal.cont2discrete(system,dt=T,method='zoh')`.

**Matched pole-zero:** map poles/zeros with $z=e^{sT}$; form $G_d(z)=K_d\prod(z-z_{z_j})/\prod(z-z_{p_i})$; match DC gain $G_d(1)=G_c(0)$; add zeros at $z=-1$ if needed so numerator order is equal to or one less than denominator order. Preserves mapped pole/zero locations, stability, and DC gain; useful for dominant pole/zero preservation.

## Fast Workflows
**SS to TF:** form $sI-A$, invert, compute $C(sI-A)^{-1}B+D$, simplify, poles from denominator/$\det(sI-A)$. **CT stability:** TF poles for BIBO, $A$ eigenvalues for internal, watch cancellations, Lyapunov $A^TP+PA=-Q$. **Linearise:** solve equilibrium, compute/evaluate Jacobians, write incremental model. **Discretise:** choose $T$, compute $G=e^{AT}$, $H=\int_0^Te^{A\lambda}d\lambda B$ or $A^{-1}(G-I)B$ if valid, keep $C,D$. **Pole placement:** check controllability, choose/map poles, match characteristic polynomial, verify. **Integral action:** decide integrated signal, add state(s), build augmented matrices, check controllability, design $K_z$, verify steady-state error. **DLQR:** check controllability, choose $Q,R$, solve DARE, compute $K$, verify poles/input, retune. **Observer:** check observability, choose observer poles, compute $L$ by duality, verify $G-LC$. **KF:** estimate $R$, choose/tune $Q$, collect residuals, check mean/whiteness/variance, iterate.

## Common Exam Traps
CT stable means $\Re(s)<0$; DT stable means $|z|<1$. Map desired CT poles to DT poles using $z=e^{sT}$. Do not confuse state matrices $G,H$ with transfer functions. Do not use $H=A^{-1}(G-I)B$ when $A$ is singular. $C,D$ usually unchanged in exact sampled state-space models. DLQR theorem uses $(G,V)$ where $Q=V^TV$, not sensor pair $(G,C)$. LQR does not handle saturation explicitly. Very fast observer poles amplify measurement noise. BIBO stability does not guarantee internal stability if unstable cancellations exist. Linearise at the actual equilibrium. Integral action increases system order and requires augmented controllability. Kalman $Q$ is process noise covariance; LQR $Q$ is state penalty.

## Transform/Command Mini-Reference
**Laplace:** $\delta(t)\leftrightarrow1$, $1(t)\leftrightarrow1/s$, $t\leftrightarrow1/s^2$, $t^n\leftrightarrow n!/s^{n+1}$, $e^{at}\leftrightarrow1/(s-a)$, $\sin\omega t\leftrightarrow\omega/(s^2+\omega^2)$, $\cos\omega t\leftrightarrow s/(s^2+\omega^2)$, $e^{at}\sin\omega t\leftrightarrow\omega/((s-a)^2+\omega^2)$, $e^{at}\cos\omega t\leftrightarrow(s-a)/((s-a)^2+\omega^2)$.

**MATLAB/Python:** `G=expm(A*T)`; `H=inv(A)*(G-eye(size(A)))*B` only if $A$ invertible; `[G,H]=c2d(A,B,T)`; `K=place(G,H,poles)`; `L=place(G',C',observer_poles)'`; `P=solve_discrete_are(G,H,Q,R)`; `K=inv(R+H.T@P@H)@(H.T@P@G)`; `c2d(Gc,T,'zoh'|'tustin'|'matched')`; `signal.cont2discrete(system,dt=T,method='zoh'|'bilinear')`.
