# Direct Design Approach

## Definition
- **Direct design** means:
  - first derive an **exact discrete-time model** of the plant
  - then design the controller **entirely in the discrete domain**

## What It Is Not
- It is **not emulation/equivalence**.
- We do **not** first design a continuous controller and then approximate it digitally.

## Main Steps
1. Find an exact discrete-time system model from the continuous-time system.
2. Design a discrete controller from performance requirements.
3. Verify the design through analysis, simulation, or experiment.

## Direct Design Paths
- The lecture highlights two broad paths:
  - **state feedback**
  - **classical design methods** in the discrete domain

## Direct Design Logic
$$
\text{continuous plant} \xrightarrow{\text{exact discretisation}} \text{discrete model} \xrightarrow{\text{design}} \text{digital controller}
$$

## Why It Is Useful
- The controller is designed for the **actual sampled model**.
- Pole locations are interpreted in the **$z$-plane**.
- This can allow lower sampling rates than some emulation-based approaches.

## Design Targets
- Desired performance is linked to:
  - settling time
  - rise time
  - overshoot
  - damping ratio
  - pole locations

## Classical Discrete Path
- The lecture mentions that classical discrete design can use:
  - discrete transfer functions
  - root locus ideas
  - compensators such as lead, lag, or PID
- In this unit, the main emphasis is still [[Discrete State Feedback]].

## Links
- [[Discrete State Feedback]]
- [[State Feedback Design Procedure]]
- [[Pole Placement Gain Methods]]
- [[Example 1 - Mass Spring Damper Direct Design]]

## Visual Placeholders
![[Direct Design Block Diagram.png|400]]
