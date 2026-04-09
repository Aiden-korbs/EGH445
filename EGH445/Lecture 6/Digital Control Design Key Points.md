# Digital Control Design Key Points

## High-Level Takeaways
- **Controllability** and **observability** are still central in discrete time.
- In discrete systems, we work with **sequences** instead of continuous signals.
- The sampling time can affect controllability and observability properties.

## Direct Design Summary
- Start with the **continuous-time system**.
- Obtain an **explicit discrete-time model**.
- Design the controller for that discrete model directly.

## Main Design Methods Mentioned
- **State feedback**
- **Observer design** as a related extension
- **Classical discrete root locus** as a parallel design path

## State Feedback Summary
- The control law
$$
u(kT)=-Kx(kT)
$$
can be used to place closed-loop poles at chosen locations in the $z$-plane.
- For fixed non-zero reference tracking, use an added **feedforward gain**:
$$
K_r
$$

## Why Transforms Matter
- When the system is not already in phase-variable form, use a transformation matrix:
$$
x=Pz
$$
to simplify gain calculation.

## Sampling Insight
- Direct design can sometimes work with lower sampling rates than emulation/equivalence approaches because the controller is designed around the actual sampled model.

## Comprehension Exercise Theme
- The lecture ends by pushing the ideas toward a more realistic application:
  - digital roll control / autopilot design
  - model the plant
  - analyse the open and closed loop
  - design a state-feedback controller from desired damping and natural frequency

## Exam-Relevant Mindset
- Be able to:
  - test controllability and observability
  - write the discrete state-feedback model
  - form and use the desired characteristic equation
  - compute or explain $K$
  - explain why $K_r$ is needed for fixed non-zero references

## Links
- [[Digital Control Design 1]]
- [[Discrete State Feedback]]
- [[Feedforward Gain for Reference Tracking]]
