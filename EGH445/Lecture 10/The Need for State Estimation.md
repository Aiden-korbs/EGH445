# The Need for State Estimation

← Back to [[State Estimation: Observers and Output Feedback]]

## The Problem

All previously designed controllers assume full state availability:

- **Pole Placement**: $u(kT) = -Kx(kT)$
- **LQR**: $u(kT) = -Kx(kT)$
- **Integral Action**: $u(kT) = -K_x x(kT) - K_q q(kT)$

In practice, we often **cannot measure all states directly** and only have access to outputs:

$$y(kT) = Cx(kT) + Du(kT)$$

## Key Question

How can we implement state-feedback $u(kT) = -Kx(kT)$ when $x(kT)$ is not directly measured?

## Can We Simply Invert C?

Assuming $D = 0$:

$$\hat{x}(kT) = C^{-1}y(kT)$$

This is **not possible in general** because:

- $C \in \mathbb{R}^{p \times n}$ is often not square
- When $p < n$ (fewer outputs than states), $C$ has no inverse

## Example: Underdetermined System

Two states ($n = 2$), one output ($p = 1$):

$$\begin{bmatrix} \dot{x}_1(t) \\ \dot{x}_2(t) \end{bmatrix} = \begin{bmatrix} 0 & 1 \\ 0 & -0.1 \end{bmatrix} \begin{bmatrix} x_1(t) \\ x_2(t) \end{bmatrix} + \begin{bmatrix} 0 \\ 1 \end{bmatrix} u(t)$$

$$y(t) = \begin{bmatrix} 1 & 0 \end{bmatrix} \begin{bmatrix} x_1(t) \\ x_2(t) \end{bmatrix} = x_1(t)$$

We can measure $x_1(t)$ directly, but $x_2(t)$ (velocity) is **not measurable**. We need an estimator.

## Why Not Just Simulate?

An open-loop observer copies the system dynamics:

$$\hat{x}(kT+T) = G\hat{x}(kT) + Hu(kT)$$

But the estimation error $e(kT) = x(kT) - \hat{x}(kT)$ evolves as:

$$e(kT+T) = Ge(kT)$$

**Problem**: Error dynamics depend on the system matrix $G$. If $G$ has unstable eigenvalues, the estimation error diverges regardless of initial estimate — even if $G$ is stable, convergence may be too slow for effective control.

## Solution

Use the measured output $y(kT)$ to correct the state estimate — this leads to the [[Discrete-Time Luenberger Observer]].
