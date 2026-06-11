# Practical Considerations: Observers and Output Feedback

## Overview

This lecture bridges the gap between ideal control design and real-world implementation, covering state estimation trade-offs, LQR and Kalman Filter tuning, and methods for converting continuous-time controllers to discrete-time equivalents.

## Map of Content

- [[Practical Considerations - Lecture]] — Lecture overview and topics covered
- [[State vs Output Feedback]] — When to measure states vs estimate them
- [[Observer Trade-offs]] — Noise amplification, computational load, certainty equivalence
- [[LQR Tuning Q and R]] — Bryson's rule, relative weights, tuning strategies
- [[LQR Limitations]] — Model accuracy, constraints, implicit pole placement
- [[Kalman Filter Tuning Challenge]] — Why Q/R are unknown, consequences of wrong ratios
- [[Kalman Filter Tuning Strategies]] — Choosing R from datasheets, choosing Q by insight
- [[Residual Analysis for KF Tuning]] — Residual properties, ACF workflow, tuning interpretation
- [[Emulation vs Direct Design]] — Emulation strategy, comparison table
- [[Tustin Bilinear Transform]] — Derivation, transformation rule, frequency warping
- [[Zero-Order Hold Equivalence]] — Staircase assumption, ZOH transform rule
- [[Matched Pole-Zero Method]] — Pole/zero mapping, DC gain matching, Nyquist zeros
- [[Worked Example: Discretising a Lead Controller]] — Full derivations for all 3 methods at T=1.0s
