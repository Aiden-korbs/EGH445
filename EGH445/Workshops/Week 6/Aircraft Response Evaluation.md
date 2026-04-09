# Aircraft Response Evaluation

## Purpose
- After designing the controller, the workshop evaluates response to a disturbance.
- Example disturbance:
  - change in angle caused by wind or atmospheric effects

## Evaluation Idea
- Simulate the response.
- Compare behaviour under different controller choices.
- Re-design if performance is not acceptable.

## Response Cases Shown
| Case | Summary |
|---|---|
| **Stable, worse performance** | angle and speed changes are large, oscillation lasts for more than $1$ minute |
| **Stable, better performance** | angle and speed changes are smaller, some oscillation remains for about $1$ minute |
| **Stable, good performance** | angle and speed changes are small, oscillation settles in less than $10$ seconds |

## Practical Insight
- Stability alone is not enough.
- The workshop emphasises comparing:
  - oscillation magnitude
  - settling speed
  - disturbance recovery quality

## Links
- [[Aircraft State Feedback Design]]
- [[Aircraft Performance Objectives]]
- [[6DOF Aircraft Running Example]]

## Visual Placeholders
![[Aircraft Response Comparison.png|400]]
