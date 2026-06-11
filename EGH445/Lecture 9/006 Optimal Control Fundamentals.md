# Optimal Control Fundamentals

## What Does "Optimal" Mean?

Optimal means best, but best in terms of what?

- Best in terms of performance?
- Best in terms of low control effort?
- Best in terms of a generalised cost?

## Key Idea

Instead of choosing pole locations, you define what constitutes good performance via a **cost function** $J$.

The controller then minimises this cost function subject to the system dynamics.

## The Discrete-Time Optimal Control Problem

Given system dynamics:

$$x(kT + T) = G x(kT) + H u(kT), \quad x(0) = x_0$$

Find $u(kT)$ that minimises the **Cost Function** (Performance Index):

$$J = \sum_{k=0}^{\infty} \left( x(kT)^\top Q x(kT) + u(kT)^\top R u(kT) \right)$$

where $Q \succeq 0$ and $R \succ 0$.

This is an infinite-horizon cost function where:

- $Q$ is the state penalty matrix
- $R$ is the control penalty matrix

The solution to this problem is the **Linear Quadratic Regulator (LQR)**.

## Quadratic Forms and Positive Definiteness

For a square matrix $P$ and vector $x$, the product $x^\top P x$ is a scalar called a **quadratic form**.

### Positive Semi-Definite ($Q \succeq 0$)

$Q \succeq 0$ means $Q$ is positive semi-definite, i.e., $x^\top Q x \geq 0$ for all $x \in \mathbb{R}^n$.

### Positive Definite ($R \succ 0$)

$R \succ 0$ means $R$ is positive definite, i.e., $x^\top R x > 0$ for all $x \in \mathbb{R}^n$ and $x \neq 0$.

A symmetric matrix $P$ is positive definite if and only if:

- All its eigenvalues are positive
- All its principal minors are positive

For a $3 \times 3$ matrix:

$$P = \begin{bmatrix} p_{1,1} & p_{1,2} & p_{1,3} \\ p_{2,1} & p_{2,2} & p_{2,3} \\ p_{3,1} & p_{3,2} & p_{3,3} \end{bmatrix} \succ 0 \iff p_{1,1} > 0, \quad \det\begin{bmatrix} p_{1,1} & p_{1,2} \\ p_{2,1} & p_{2,2} \end{bmatrix} > 0, \quad \det(P) > 0$$

## Cost Function Expansion

The cost function is a quadratic form in the state and control variables. For $x(k) = [x_1(k), x_2(k)]^\top$ and $u(k) = [u_1(k), u_2(k)]^\top$:

$$J = \sum_{k=0}^{\infty} \left( q_{1,1}x_1(k)^2 + q_{1,2}x_1(k)x_2(k) + q_{2,1}x_2(k)x_1(k) + q_{2,2}x_2(k)^2 + r_{1,1}u_1(k)^2 + r_{1,2}u_1(k)u_2(k) + r_{2,1}u_2(k)u_1(k) + r_{2,2}u_2(k)^2 \right)$$

You have freedom to tune the individual weights $q_{i,j}$ and $r_{i,j}$ in the cost function.

## Key Takeaways

- Optimal control replaces pole placement with a cost-based formulation
- The cost function $J$ quantifies performance as a weighted sum of state and control effort
- $Q \succeq 0$ weights state deviations; $R \succ 0$ weights control effort
- The relative sizes of $Q$ and $R$ encode the performance trade-off
- The solution is the LQR, which minimises $J$ subject to system dynamics

## Related

- [[005 Pole Placement Control Effort Trade-offs]]
- [[007 Discrete Linear Quadratic Regulator DLQR]]
- [[011 DLQR Tuning]]
