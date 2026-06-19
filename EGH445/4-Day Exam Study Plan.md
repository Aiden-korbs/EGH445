You do not need to learn the unit perfectly. You need to become good enough at the repeated exam patterns: modelling, stability, linearisation, discretisation, controllability/observability, state feedback, observers, and basic LQR/Kalman/MPC concepts.

## Where To Start
 
Start with the exam tasks, not the lecture order.

Use these files first:

- `EGH445 Exam Resource Sheet - Compact.md`
- `EGH445 Exam Resource Sheet.md`
- `Exam Practice/Additional Practice Questions.md`
- PDFs in `Exam Practice/`

Best first move:

1. Open `EGH445 Exam Resource Sheet - Compact.md`.
2. Spend 45 minutes reading Sections 1-5.
3. Then attempt Problem 1 and Problem 2 from `Exam Practice/Additional Practice Questions.md`.

---

## Priority 1: Core Skills

These are the topics most likely to give you marks quickly.

### 1. State-Space Basics

Know the standard forms:

$$
\dot{x}=Ax+Bu
$$

$$
y=Cx+Du
$$

You should be able to:

- Identify states, inputs, and outputs.
- State matrix dimensions.
- Convert a simple ODE into state-space form.
- Convert state-space to transfer function:

$$
G(s)=C(sI-A)^{-1}B+D
$$

### 2. Stability

Continuous-time stability:

- Stable if all poles/eigenvalues have negative real parts.
- Check $\Re(\lambda_i)<0$.

Discrete-time stability:

- Stable if all poles/eigenvalues are inside the unit circle.
- Check $|z_i|<1$.

Know the difference:

- BIBO stability is about bounded input giving bounded output.
- Internal stability is about all internal states decaying.
- Internal stability is stronger.

### 3. Linearisation

Workflow:

1. Find equilibrium:

$$
0=f(\bar{x},\bar{u})
$$

2. Define small deviations:

$$
\delta x=x-\bar{x}
$$

$$
\delta u=u-\bar{u}
$$

3. Compute Jacobians:

$$
A=\left.\frac{\partial f}{\partial x}\right|_{\bar{x},\bar{u}}
$$

$$
B=\left.\frac{\partial f}{\partial u}\right|_{\bar{x},\bar{u}}
$$

4. Write:

$$
\delta\dot{x}=A\delta x+B\delta u
$$

Exam trap:

- Evaluate at the actual equilibrium, not automatically at the origin.

### 4. Discretisation

Exact sampled state-space model:

$$
x(kT+T)=Gx(kT)+Hu(kT)
$$

where:

$$
G=e^{AT}
$$

$$
H=\int_0^T e^{A\lambda}B\,d\lambda
$$

If $A$ is invertible:

$$
H=A^{-1}(G-I)B
$$

Pole mapping:

$$
z=e^{sT}
$$

### 5. Controllability And Observability

Controllability matrix:

$$
\mathcal C=\begin{bmatrix}H&GH&\cdots&G^{n-1}H\end{bmatrix}
$$

System is controllable if:

$$
\operatorname{rank}(\mathcal C)=n
$$

Observability matrix:

$$
\mathcal O=\begin{bmatrix}C\\CG\\\vdots\\CG^{n-1}\end{bmatrix}
$$

System is observable if:

$$
\operatorname{rank}(\mathcal O)=n
$$

Meaning:

- Controllability: can move the states using inputs.
- Observability: can reconstruct the states from outputs.

### 6. State Feedback

State feedback law:

$$
u=-Kx
$$

Closed-loop dynamics:

$$
x(k+1)=(G-HK)x(k)
$$

Closed-loop poles are eigenvalues of:

$$
G-HK
$$

Pole placement workflow:

1. Check controllability.
2. Choose desired discrete poles.
3. If poles are continuous, map using $z=e^{sT}$.
4. Match $\det(zI-(G-HK))$ to the desired polynomial.
5. Solve for $K$.

### 7. Observers

Observer equation:

$$
\hat{x}(k+1)=G\hat{x}(k)+Hu(k)+L(y(k)-\hat{y}(k))
$$

where:

$$
\hat{y}(k)=C\hat{x}(k)
$$

Error dynamics:

$$
e(k+1)=(G-LC)e(k)
$$

Design idea:

- Choose $L$ so eigenvalues of $G-LC$ are stable.
- Observer poles are usually faster than controller poles.

### 8. LQR, Kalman, MPC Concepts

LQR:

- Balances state error and control effort.
- Cost:

$$
J=\sum_{k=0}^{\infty}\left(x^TQx+u^TRu\right)
$$

- Bigger $Q$: faster, more aggressive, more control effort.
- Bigger $R$: slower, less control effort.

Kalman filter:

- Estimates states with noise.
- $Q$ is process noise covariance.
- $R$ is measurement noise covariance.
- Larger $R$: trust measurements less, trust model more.

MPC:

- Solves an optimisation problem online.
- Handles constraints directly.
- More computationally expensive than LQR.

---

## 4-Day Study Plan

## Day 1: Foundations

Goal: understand the language of the unit.

Study:

- State-space form
- Transfer functions
- Stability
- Linearisation
- Controllability and observability

Do:

1. Read Sections 1-5 of `EGH445 Exam Resource Sheet - Compact.md`.
2. Work through simple examples of:
   - ODE to state space
   - Eigenvalue stability
   - Finding equilibrium points
   - Computing Jacobians
   - Rank tests for controllability and observability
3. Attempt Problem 1 and Problem 2 from `Exam Practice/Additional Practice Questions.md`.

If stuck, prioritise:

- Stability tests
- Linearisation workflow
- Controllability matrix
- Observability matrix

## Day 2: Digital Control

Goal: understand discrete-time control design.

Study:

- Exact discretisation
- $z=e^{sT}$ mapping
- Discrete-time stability
- State feedback
- Pole placement
- Integral action

Do:

1. Read Sections 4-6 of the compact sheet.
2. Practise mapping poles:

$$
z=e^{sT}
$$

3. Practise checking whether $G-HK$ is stable.
4. Practise designing $K$ for a 2-state system.
5. Attempt Practice Paper A Problem 3.

Key idea:

- Most digital control questions come down to finding the closed-loop matrix and checking its eigenvalues.

## Day 3: End-Semester Topics

Goal: cover observer, LQR, Kalman, MPC, and discretisation-method concepts.

Study:

- DLQR
- Observer design
- Separation principle
- Kalman filter tuning
- Tustin, ZOH, matched pole-zero
- MPC vs LQR

Do:

1. Read Sections 7-9 of the compact sheet.
2. Memorise:

$$
K=(R+H^TPH)^{-1}H^TPG
$$

3. Memorise observer error dynamics:

$$
e(k+1)=(G-LC)e(k)
$$

4. Attempt Practice Paper B Question 1 and Question 2.
5. Write short answers for:
   - LQR vs MPC
   - Kalman vs Luenberger observer
   - Why observer poles are faster than controller poles
   - Why LQR does not handle saturation directly

## Day 4: Exam Simulation And Weak Spots

Goal: practise under exam conditions and patch gaps.

Do:

1. Attempt one full practice paper from `Additional Practice Questions.md`.
2. Time yourself.
3. Use the compact sheet to mark what you could and could not do.
4. Spend the final study block memorising the formulas and workflows below.

Final memorisation list:

- CT stability: $\Re(\lambda)<0$
- DT stability: $|z|<1$
- Pole mapping: $z=e^{sT}$
- Transfer function: $C(sI-A)^{-1}B+D$
- Controllability matrix
- Observability matrix
- Linearisation Jacobians
- Closed-loop matrix: $G-HK$
- Observer error matrix: $G-LC$
- DLQR gain formula
- Integral action augmentation idea
- Kalman $Q$ vs $R$

---

## What To Do If You Are Overwhelmed

If you only have time to master five things, master these:

1. Stability tests
2. Linearisation
3. Controllability and observability rank tests
4. State feedback closed-loop matrix $G-HK$
5. Observer error matrix $G-LC$

These appear repeatedly and can collect marks even if you cannot finish the whole exam.

## Minimum Viable Exam Strategy

In the exam:

1. Do short-answer conceptual questions first.
2. Then do stability/rank-test questions.
3. Then do linearisation questions.
4. Then attempt state feedback or observer design.
5. Leave heavy algebra or long controller derivations until later.

Always write:

- What test you are using
- The relevant matrix
- The condition for success
- Your conclusion in words

Even if the arithmetic is wrong, this gives partial marks.
