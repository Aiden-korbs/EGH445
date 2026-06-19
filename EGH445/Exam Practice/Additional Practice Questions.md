These questions are written to match the style, structure, topic spread, and marking patterns of the exam practice PDFs in this folder. They are intentionally different from the existing papers and are provided as question-only practice.

---

# Practice Paper A: Mid-Semester Style

## Instructions

This practice paper has a total of 3 problems. The total number of possible marks is 100.

It is recommended that you attempt all questions. All answers need to be carefully justified. Explanations of the steps used are essential. Full marks are awarded for fully justified and numerically correct solutions. Partial marks may be awarded for partially complete solutions, numerically incorrect solutions with correct method, or solutions that use clearly stated and justified assumptions consistent with the question.

---

## Problem 1

Provide a short response to the following questions (a)-(f). You may include supporting diagrams, mathematics, or examples in your responses.

(a) Explain the difference between a physical state and a redundant state in a state-space model. Give one example of each.  
**(5/100 marks)**

- A physical state is a system of which can be measured and a redundant state is a system that has multiple of the same sensors

(b) A nonlinear system has three isolated equilibrium points. Explain why the stability of one equilibrium point does not necessarily determine the stability of the others.  
**(5/100 marks)**
- Each equilibrium has different stability properties meaning each one has to be satisfied in its own way

(c) A discrete-time linear system has poles at $z=0.6$, $z=-0.8$, and $z=1.1$. Describe the expected qualitative behaviour of the system response and state whether the system is asymptotically stable.  
**(5/100 marks)**
- most likely the system is not asymptotically stable as all the poles are not |z|<1.

(d) Consider two state-space models related by $z(t)=P^{-1}x(t)$, where $P$ is nonsingular. Do the two models have the same internal stability properties? Justify your answer.  
**(5/100 marks)**
- yes

(e) Explain why a system can be BIBO stable but not internally stable. In your answer, refer to pole-zero cancellation or hidden modes.  
**(5/100 marks)**
- a system can be BIBO stable due to it having poles in the Re<0 plane however for a system to be internally stable you need to satisfy the requirement of all eigenvalues being Re<0

(f) What information does the controllability matrix provide for state feedback design? What does it mean physically if the controllability matrix is rank deficient?  
**(5/100 marks)**
- The controllability matrix describes where the system is controllable or not, where the rank needs to = n where n is number of system equations. if n != rank then the system is rank deficient 

**Total for Problem 1: 30/100 marks**

---

## Problem 2

A simplified nonlinear thermal regulation model for a high-performance battery pack is given by

$$
\dot{x}_1(t)=x_2(t)
$$

$$
\dot{x}_2(t)=-0.4x_1(t)-0.2\sin(x_2(t))+0.5u(t)
$$

where $x_1(t)$ is the temperature deviation from nominal operating temperature, $x_2(t)$ is the rate of temperature change, and $u(t)$ is the cooling input.

(a) Find the equilibrium state $(\bar{x}_1,\bar{x}_2)$ corresponding to a constant input $\bar{u}=2$.  
**(8/100 marks)**
-  $(\bar{x}_1,\bar{x}_2)$ = (2.5,0)

(b) Linearise the nonlinear system dynamics around the equilibrium point found in part (a). Express the result in the standard incremental state-space form

$$
\delta\dot{x}=A\delta x+B\delta u
$$

clearly stating $A$ and $B$.  
**(10/100 marks)**

- $$A= \begin{bmatrix} 0 & 1 \\ -0.4 & -0.2\cos(x_2) \end{bmatrix}$$
- $$B= \begin{bmatrix} 0 \\ 0.5 \end{bmatrix}$$
- $$
\delta\dot{x}= \begin{bmatrix} 0 & 1 \\ -0.4 & -0.2\cos(x_2) \end{bmatrix}\delta x+\begin{bmatrix} 0 \\ 0.5 \end{bmatrix}\delta u
$$

- subbing eq state
- $$
\delta\dot{x}= \begin{bmatrix} 0 & 1 \\ -0.4 & -0.2 \end{bmatrix}\delta x+\begin{bmatrix} 0 \\ 0.5 \end{bmatrix}\delta u
$$
(c) Analyse the local stability of the equilibrium point using the linearised model. Clearly state any assumptions made.  
**(6/100 marks)**
- det(λI−A)=0

gives:

$λ2+0.2λ+0.4=0\lambda^2+0.2\lambda+0.4=0λ2+0.2λ+0.4=0$

Solving:

$λ=−0.1±0.624j\lambda = -0.1 \pm 0.624jλ=−0.1±0.624j$

The real part is:

$Re⁡(λ)=−0.1<0\operatorname{Re}(\lambda)=-0.1<0Re(λ)=−0.1<0$

Therefore system is internally stable 

(d) The battery management system is implemented digitally using sampling time $T=0.5$ seconds. Using the first-order approximation $G\approx I+AT$ and $H\approx BT$, obtain an approximate discrete-time model for the linearised dynamics. Comment on whether this approximation is likely to be reliable.  
**(6/100 marks)**

**Total for Problem 2: 30/100 marks**

---

## Problem 3

An automated warehouse vehicle has a simplified lateral steering model given by

$$
x(kT+T)=Gx(kT)+Hu(kT)
$$

$$
y(kT)=Cx(kT)
$$

where

$$
G=\begin{bmatrix}1&0.4\\0&0.7\end{bmatrix},\quad
H=\begin{bmatrix}0.08\\0.3\end{bmatrix},\quad
C=\begin{bmatrix}1&0\end{bmatrix}
$$

The states are lateral position error and heading-rate error, and the input is steering command.

(a) Determine whether the system is completely state controllable. Show your working.  
**(8/100 marks)**

(b) Determine whether the system is completely observable from the measured output $y(kT)$. Show your working.  
**(8/100 marks)**

(c) Design a state feedback controller $u(kT)=-Kx(kT)$ such that the closed-loop poles are located at $z_1=0.45$ and $z_2=0.30$. Clearly state the gain $K$.  
**(18/100 marks)**

(d) If the steering actuator saturates at $|u(kT)|\leq 0.25$, explain how this may affect the performance predicted in part (c). Suggest one modelling or control design change that could address this issue.  
**(6/100 marks)**

**Total for Problem 3: 40/100 marks**

---

# Practice Paper B: End-Semester Style

## Instructions

This practice paper has a total of 3 questions. You must answer all 3 questions. The total number of possible marks is 100. Each question can be addressed independently. It is recommended that you use perusal time to decide the order in which you will solve the questions.

All answers need to be justified. Explanations of the steps used are essential and should be clearly shown. Any assumptions made should be consistent with the question, clearly stated, and justified.

---

## Question 1

Provide a short response to the following questions (a)-(h). You may include supporting diagrams, mathematics, or examples in your responses.

(a) Describe how the sample period $T$ affects the discrete-time pole locations obtained from continuous-time poles.  
**(4 marks)**

(b) Explain the difference between state feedback control with a feedforward gain and state feedback control with integral action.  
**(4 marks)**

(c) In discrete-time control design, why must all closed-loop poles lie inside the unit circle?  
**(3 marks)**

(d) What is the internal model principle, and why is an integrator useful for rejecting constant disturbances?  
**(4 marks)**

(e) In DLQR design, what are the roles of the matrices $Q$ and $R$? Explain the expected effect of increasing $R$ while keeping $Q$ fixed.  
**(4 marks)**

(f) The DLQR stability theorem uses observability of $(G,V)$ where $Q=V^TV$. Explain why this is not the same as observability of $(G,C)$.  
**(4 marks)**

(g) In Kalman filter design, what does the measurement noise covariance matrix $R$ represent? How would increasing $R$ affect the estimator behaviour?  
**(4 marks)**

(h) Compare the Tustin bilinear transform and the matched pole-zero method for converting a continuous-time controller to a discrete-time controller.  
**(3 marks)**

**Total for Question 1: 30 marks**

---

## Question 2

An autonomous surface vessel uses a digital controller to regulate its yaw angle while travelling at low speed. A simplified discrete-time model is

$$
x(kT+T)=Gx(kT)+Hu(kT)
$$

$$
y(kT)=Cx(kT)
$$

where

$$
G=\begin{bmatrix}0.9&0.2\\0&0.6\end{bmatrix},\quad
H=\begin{bmatrix}0.05\\0.4\end{bmatrix},\quad
C=\begin{bmatrix}1&0\end{bmatrix}
$$

The states are yaw angle error and yaw-rate error, and the input is the rudder command.

(a) Design a full-order discrete-time state observer for the system such that the equivalent continuous-time observer poles are located at $p_1=-4$ and $p_2=-6$. Assume the sampling time is $T=0.25$ seconds. State any assumptions made.  
**(14 marks)**

(b) Write the observer-based state feedback controller equations for the system using a controller gain $K$ and observer gain $L$.  
**(6 marks)**

(c) Write the combined closed-loop dynamics in terms of the plant state $x(kT)$ and estimation error $e(kT)=x(kT)-\hat{x}(kT)$. Explain how the separation principle applies.  
**(10 marks)**

**Total for Question 2: 30 marks**

---

## Question 3

A robotic inspection platform uses a discrete-time model for vertical positioning near a pipe wall:

$$
x(kT+T)=Gx(kT)+Hu(kT)
$$

$$
y(kT)=Cx(kT)
$$

where

$$
G=\begin{bmatrix}1&1\\0&0.5\end{bmatrix},\quad
H=\begin{bmatrix}0\\1\end{bmatrix},\quad
C=\begin{bmatrix}1&0\end{bmatrix}
$$

The states are position error and velocity error, and the input is a vertical thrust command.

(a) Provide an analysis of the model that would help an engineering team design a digital position regulation controller. Your answer should include stability, controllability, observability, and any practical interpretation of the states and input.  
**(10 marks)**

(b) A state feedback controller is proposed:

$$
u(kT)=-0.2x_1(kT)-0.7x_2(kT)
$$

Determine the expected closed-loop performance by analysing the closed-loop poles. Justify whether the controller is stabilising.  
**(10 marks)**

(c) The engineering team wants to redesign the controller so that the response balances state deviations and control effort. Design a DLQR controller using

$$
Q=\begin{bmatrix}4&0\\0&1\end{bmatrix},\quad
R=2,
$$

and the supplied Riccati solution

$$
P=\begin{bmatrix}7&2\\2&4\end{bmatrix}.
$$

You must show all design steps, but you do not need to solve the Riccati equation.  
**(12 marks)**

(d) The platform must hold a fixed non-zero height offset in the presence of a constant downward disturbance. Explain why basic state feedback may not achieve zero steady-state error. Propose an augmented controller structure that addresses the issue.  
**(8 marks)**

**Total for Question 3: 40 marks**

---

# Optional Challenge Questions

These shorter questions follow the same topic style but are not part of the 100-mark papers above.

## Challenge 1: Controller Discretisation

A continuous-time controller is given by

$$
G_c(s)=3\frac{s+2}{s+12}.
$$

(a) Use the matched pole-zero method to derive a discrete-time controller $G_d(z)$ for sampling time $T=0.1$ seconds. Match the DC gain.  
**(10 marks)**

(b) Explain whether this method preserves stability and why.  
**(4 marks)**

(c) Explain one reason why Tustin's method may produce a different frequency response from the matched pole-zero method.  
**(4 marks)**

## Challenge 2: Kalman Filter Tuning

A drone altitude estimator uses a Kalman filter. During testing, the residual sequence $e(kT)=y(kT)-\hat{y}^-(kT)$ has a non-zero mean and strong positive autocorrelation.

(a) Explain what each of these residual properties suggests about the estimator or model.  
**(6 marks)**

(b) Suggest a practical tuning workflow for improving the Kalman filter.  
**(6 marks)**

(c) If the sensor datasheet reports measurement noise standard deviation $\sigma_v=0.08$ m, what value would you initially use for a scalar measurement covariance $R$?  
**(3 marks)**
