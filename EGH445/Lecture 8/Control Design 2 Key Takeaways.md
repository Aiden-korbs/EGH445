# Control Design 2 Key Takeaways

## Main Lessons
- **State feedback** alone stabilises but does not automatically reject constant disturbances.
- **Feedforward disturbance cancellation** works only when the disturbance and plant model are known accurately.
- **Integral action** gives zero steady-state error for constant references and rejects constant input disturbances.
- **Tracking** a time-varying reference is harder than regulation.
- The [[Internal Model Principle]] explains what extra controller dynamics are needed.

## Signal-to-Controller Matching
| Signal to reject/track | Required embedded dynamics |
|---|---|
| Constant | integrator |
| Ramp | repeated integrator |
| Sinusoid | oscillator model |

## Design Mindset
- Do not rely on gain tuning alone.
- Ask:
  - what signal class must be followed?
  - what uncertainty is present?
  - what dynamics must be embedded inside the controller?

## Links
- [[Disturbances in Discrete-Time State Feedback]]
- [[Integral Action for Disturbance Rejection]]
- [[Tracking vs Regulation]]
- [[Internal Model Principle]]

## Visual Placeholders
![[Control Design 2 Summary.png|400]]
