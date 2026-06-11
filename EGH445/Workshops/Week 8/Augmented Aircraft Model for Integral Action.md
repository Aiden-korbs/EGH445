# Augmented Aircraft Model for Integral Action

## Why the Model Is Augmented
- Week 8 adds **integral action** to the aircraft example.
- This increases controller order by adding an extra state.

## Important Change
- Because of augmentation:
$$
G_a \in \mathbb{R}^{5 \times 5}
$$
- So the system now has **five poles** instead of four.

## Pole Selection Note
- The original aircraft model had four poles, usually described via:
  - two damping ratios
  - two natural frequencies
- After augmentation, an **additional pole** must be chosen.

## Example Choice
- The workshop suggests placing the additional pole at:
$$
10 \times \min\left(\Re(\text{desired poles})\right)
$$
as one candidate choice for a well-damped design.

## Gain Computation
- The controller gain is found with MATLAB:
```matlab
z = place(Ga, Ha, desired_poles)
```

## Example Gain Shown
- For the well-damped design, the workshop shows:
$$
K_z = [-87.59\; -7.33\; -83.07\; 1423.8\; 32.23]
$$

## Design Interpretation
- The extra pole must usually be placed sufficiently fast so the integral dynamics help steady-state performance without badly degrading the transient.

## Links
- [[6DOF Aircraft Workshop Example]]
- [[Integral Action in Discrete-Time Control]]
- [[Aircraft Response Evaluation]]

## Visual Placeholders
![[Aircraft Augmented Gain Design.png|400]]
