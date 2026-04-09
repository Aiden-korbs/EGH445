# Aircraft Performance Objectives

## Core Idea
- The aircraft system has **$4$ poles**, so the workshop frames the design in terms of:
  - two damping ratios
  - two natural frequencies

## Engineering Basis
- The pole choices are tied to practical concerns such as:
  - flying qualities
  - certification rules
  - comfort and handling
  - manoeuvrability

## Example Objective Sets
### A. Well Damped
$$
\omega_{n,\mathrm{sp}} = 2,\qquad \omega_{n,\mathrm{lp}} = 0.5
$$
$$
\zeta_{\mathrm{sp}} = 1.6,\qquad \zeta_{\mathrm{lp}} = 0.7
$$

### B. Semi Damped
$$
\omega_{n,\mathrm{sp}} = 3,\qquad \omega_{n,\mathrm{lp}} = 0.1
$$
$$
\zeta_{\mathrm{sp}} = 0.9,\qquad \zeta_{\mathrm{lp}} = 0.7
$$

## Discrete-Time Conversion
- Performance is usually specified in continuous time.
- The workshop reminds you to map the poles into the discrete domain using:
$$
z = e^{sT}
$$

## Interpretation
- The designer may have some freedom in choosing non-dominant poles.
- Dominant-pole selection is tied to the expected aircraft handling response.

## Links
- [[Aircraft State Feedback Design]]
- [[Aircraft Response Evaluation]]
- [[Regulation in Discrete Control]]

## Visual Placeholders
![[Aircraft Performance Objective Selection.png|400]]
