← Back to [[EGH445 Modern Control]]

# Digital Control Design 2

## Map of Content
- [[Disturbances in Discrete-Time State Feedback]]
- [[Feedforward Disturbance Compensation]]
- [[Integral Action for Disturbance Rejection]]
- [[Augmented System for Integral Action]]
- [[Non-Zero Regulation with Integral Action]]
- [[Tracking vs Regulation]]
- [[Internal Model Principle]]
- [[Dynamic Extension for Step Ramp and Sinusoidal References]]
- [[Sinusoidal Tracking by Augmentation]]
- [[Mass-Spring-Damper Design 2 Example]]
- [[Control Design 2 Key Takeaways]]

## Scope
- This lecture extends [[Digital Control Analysis]] and [[Digital Control Design 1]].
- Main themes:
  - rejecting **unknown disturbances**
  - using **integral action**
  - moving from **regulation** to **tracking**
  - applying the **internal model principle**

## Big Picture
- Plain state feedback can stabilise a system, but may not remove steady-state error under constant disturbances.
- **Feedforward disturbance cancellation** can work only when the disturbance and model are known accurately.
- **Integral action** improves robustness to constant references and constant disturbances.
- For dynamic references such as ramps and sinusoids, the controller must embed the relevant signal dynamics using the [[Internal Model Principle]].

## Visual Placeholders
![[Design 2 Overview.png|400]]
![[Disturbance Integral Tracking Roadmap.png|400]]
