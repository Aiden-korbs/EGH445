# Dynamic Extension for Step Ramp and Sinusoidal References

## Step Reference
- Use one error-integrating state:
$$
q(kT+T) = q(kT) + e(kT)
$$
- This corresponds to embedding step dynamics.

## Ramp Reference
- Use two stacked integrating states:
$$
q_1(kT+T) = q_1(kT) + e(kT)
$$
$$
q_2(kT+T) = q_2(kT) + q_1(kT)
$$

## Sinusoidal Reference
- Use an oscillator driven by the error:
$$
q_1(kT+T) = q_2(kT)
$$
$$
q_2(kT+T) = -q_1(kT) + 2\cos(\omega)\,q_2(kT) + e(kT)
$$

## Interpretation
| Signal Type | Internal Model Added |
|---|---|
| Step | integrator |
| Ramp | double integrator |
| Sinusoid | discrete oscillator |

## Design Principle
- The augmentation should mirror the denominator of the desired reference generator.

## Link to State-Space Design
- After defining the new states, combine them with the plant state and design a new state-feedback law on the augmented model.

## Links
- [[Internal Model Principle]]
- [[Sinusoidal Tracking by Augmentation]]
- [[Tracking vs Regulation]]

## Visual Placeholders
![[Dynamic Extension Examples.png|400]]
