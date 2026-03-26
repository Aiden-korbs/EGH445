← Back to [[EGH445 - Modern Control]]

# Digital Control Analysis

## Map of Content
- [[Sampling Time Selection]]
- [[Aliasing and Nyquist Criterion]]
- [[Tracking Effectiveness in Digital Control]]
- [[Regulation Effectiveness and Anti-Alias Filtering]]
- [[Z Transform]]
- [[Pulse Transfer Functions]]
- [[Discrete Transfer Function from Continuous Models]]
- [[Discrete Transfer Function from State Space]]
- [[Discrete-Time Stability]]
- [[s-Plane to z-Plane Mapping]]
- [[Discrete-Time System Response]]
- [[Discrete Final Value]]

## Core Theme
- This lecture focuses on **analysis of discrete-time control systems**.
- The main analysis blocks are:
  - **Sampling and aliasing**
  - **Pulse transfer functions**
  - **Stability**
  - **System response**

## Big Picture
- A digital control system samples analogue signals at intervals of $T$.
- The sample period and sample frequency are related by:
$$
T = \frac{1}{f_s}
$$
- Poor sampling can create:
  - **Aliasing**
  - **Incorrect tracking**
  - **Incorrect regulation**
  - **Potential stability degradation**
- Discrete-time analysis uses:
  - the **$\mathcal{Z}$ transform**
  - **pulse transfer functions**
  - **discrete state-space models**
  - **pole locations in the $z$-plane**

## Visuals
![[Digital Control Analysis Overview.png|400]]
![[Digital Control Architecture.png|400]]
