# Aircraft Response Evaluation

## Goal
- After designing the controller, the response should be simulated and checked against the control objectives.

## Disturbance Scenario
- The workshop evaluates a response to a disturbance such as:
  - a change in angle caused by wind
  - atmospheric variation near equilibrium
  - non-zero initial angle of attack / vertical velocity

## Comparison Shown
- Two cases are compared:
  - additional pole at
$$
10 \times \min(\Re(\text{desired poles}))
$$
  - additional pole at
$$
1.1 \times \min(\Re(\text{desired poles}))
$$

## Main Insight
- The placement of the extra pole introduced by integral action affects:
  - transient amplitude
  - oscillation level
  - settling behaviour

## Practical Conclusion
- Adding integral action improves steady-state regulation, but the extra pole must be chosen carefully.
- Faster added poles are not automatically “best”; the design still needs evaluation.

## Scenario
### Scenario
Compare two augmented aircraft controllers with different additional pole placements.

### Given
- Same aircraft plant model
- Same desired dominant pole goals
- Two different choices for the extra pole

### Steps
1. Design the augmented controller for each extra-pole choice.
2. Simulate disturbance response.
3. Compare oscillation, amplitude, and settling.
4. Decide which design offers the better trade-off.

### Final Notes
- Integral action improves regulation, but pole placement still governs transient quality.

## Links
- [[Augmented Aircraft Model for Integral Action]]
- [[6DOF Aircraft Workshop Example]]

## Visual Placeholders
![[Aircraft Response Pole Comparison.png|400]]
