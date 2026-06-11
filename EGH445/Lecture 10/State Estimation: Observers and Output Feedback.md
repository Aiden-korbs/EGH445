# State Estimation: Observers and Output Feedback

## Overview

When full state measurement is unavailable, state estimation methods reconstruct the internal state from measured outputs. This unit covers the progression from basic Luenberger observers through optimal estimation with Kalman Filters, including advanced topics like reference tracking, disturbance rejection, and nonlinear estimation.

## Map of Content

- [[The Need for State Estimation]] — Why state estimation is necessary and the observability problem
- [[Discrete-Time Luenberger Observer]] — Observer structure and error dynamics
- [[Observability]] — Condition for arbitrary eigenvalue placement in observer design
- [[Observer Design via Pole Placement]] — Designing observer gain L via pole placement and duality
- [[Output Feedback Control]] — Combining controller and observer into closed-loop system
- [[Separation Principle]] — Independent design of controller and observer gains
- [[Observer-Based Control with Reference Tracking]] — Feedforward approach for setpoint tracking
- [[Integral Action with Observers]] — Disturbance estimation for robust tracking
- [[The Kalman Filter]] — Optimal estimation for linear systems with Gaussian noise
- [[How the Kalman Filter Works]] — Predict-correct algorithm of the Kalman Filter
- [[Extended Kalman Filter]] — Handling nonlinear systems via linearisation
