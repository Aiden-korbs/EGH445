# Discrete-Time Control Design 3: Optimal Control

## Overview

This lecture introduces optimal control as a systematic alternative to pole placement, covering the Discrete Linear Quadratic Regulator (DLQR) and Model Predictive Control (MPC) for handling trade-offs, constraints, and multi-variable systems.

## Map of Content

- [[002 Review of Discrete-Time Systems]] — Review of continuous-time, discretisation, state-feedback, and pole placement
- [[003 Pole Placement: When It Works and When It Fails]] — Limitations of pole placement for higher-order, MIMO, stiff, and nonlinear systems
- [[004 Higher-Order and MIMO Pole Placement Limitations]] — Why pole placement breaks down for systems with $n > 3$ and multiple inputs/outputs
- [[005 Pole Placement Control Effort Trade-offs]] — How pole placement ignores control effort, leading to impractical or unstable designs on nonlinear systems
- [[006 Optimal Control Fundamentals]] — Core concepts of optimal control, cost functions, and the motivation for optimal control over pole placement
- [[007 Discrete Linear Quadratic Regulator DLQR]] — The DLQR formulation, optimal gain computation, and the Discrete Algebraic Riccati Equation (DARE)
- [[008 DLQR Design Procedure]] — Step-by-step procedure for designing DLQR controllers
- [[009 DLQR Stability Theorem]] — Conditions for existence and stability of the DLQR solution
- [[010 DLQR Examples]] — Scalar and MIMO DLQR design examples solved by hand and with code
- [[011 DLQR Tuning]] — Tuning the cost matrices $Q$ and $R$ to shape performance trade-offs
- [[012 LQR Limitations and Control Saturation]] — Control saturation effects and comparison of unconstrained, saturated, and MPC approaches
- [[013 Model Predictive Control MPC]] — MPC fundamentals, finite-horizon optimization, and comparison with LQR
