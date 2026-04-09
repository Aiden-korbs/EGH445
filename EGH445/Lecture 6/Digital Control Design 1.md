← Back to [[EGH445 - Modern Control]]

# Digital Control Design 1

## Concepts
- [[Controllability]]
- [[Observability]]
- [[Discrete-Time Controllability and Observability Nuances]]
- [[Direct Design Approach]]
- [[Discrete State Feedback]]
- [[State Feedback Design Procedure]]
- [[Pole Placement Gain Methods]]
- [[Regulation with Zero Reference]]
- [[Regulation with Non-Zero Reference]]
- [[Feedforward Gain for Reference Tracking]]
- [[Example 1 - Mass Spring Damper Direct Design]]
- [[MATLAB Workflow for Digital Control Design]]
- [[Digital Control Design Key Points]]

## Lecture Scope
- **Core lecture topics**:
  - controllability and observability
  - direct discrete-time design
  - state feedback
  - regulation for $r(kT)=0$
  - regulation for fixed non-zero references
- The lecture treats digital control design as a **full design process**:
  1. obtain an **exact discrete-time model**
  2. design a **discrete controller** directly in the $z$-domain or discrete state-space domain
  3. verify using **analysis, simulation, or implementation**

## Big Picture
- Direct design does **not** start with a continuous controller and then approximate it digitally.
- Instead, the process is:
$$
\text{continuous plant} \rightarrow \text{exact discrete model} \rightarrow \text{digital controller}
$$
- This means performance and pole placement are designed directly for the sampled system.

## Common Links
- [[Direct Design Approach]] connects the modelling and controller design stages.
- [[Discrete State Feedback]] gives the main control architecture used in this lecture.
- [[Pole Placement Gain Methods]] summarises the three gain-finding methods used in the examples.
- [[Feedforward Gain for Reference Tracking]] extends state feedback so the system can track a fixed non-zero reference.
