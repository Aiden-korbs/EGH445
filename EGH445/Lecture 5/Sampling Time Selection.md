# Sampling Time Selection

## Key Idea
- Choosing the sampling period $T$ is an **engineering trade-off**.
- Sampling too slowly harms performance.
- Sampling too quickly can increase:
  - cost
  - computation demand
  - measurement sensitivity
  - regulation inaccuracies

## Main Relationships
- Sample period and sample frequency:
$$
T = \frac{1}{f_s}
$$
- Angular sampling frequency may also be written as $\omega_s$.

## Design Factors
| Factor | Meaning | Effect on Sampling Choice |
|---|---|---|
| **Tracking effectiveness** | Ability to follow the reference input | Pushes $f_s$ higher |
| **Regulation effectiveness** | Ability to reject disturbances and noise | Pushes $f_s$ and filtering design higher |
| **Cost** | Hardware, sensing, and computation cost | Pushes $f_s$ lower |

## Engineering Interpretation
- Lower sampling rate:
  - cheaper hardware
  - more computation time between samples
- Higher sampling rate:
  - usually better tracking
  - better shape capture of fast-changing signals
- Practical goal:
  - sample **as slowly as performance allows**

## Rules of Thumb
- Nyquist lower bound:
$$
f_s > 2f
$$
where $f$ is the highest relevant signal frequency.
- For practical control performance, a common choice is:
$$
f_s \ge 10f
$$
- A more typical practical range is:
$$
f_s \approx 20f \text{ to } 40f
$$

## Links
- [[Aliasing and Nyquist Criterion]]
- [[Tracking Effectiveness in Digital Control]]
- [[Regulation Effectiveness and Anti-Alias Filtering]]

## Visuals
![[Sampling Time Tradeoff.png|400]]
