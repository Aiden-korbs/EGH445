# Discrete Final Value

## Purpose
- For a **stable** discrete-time system, the final steady-state value can be found directly in the $z$-domain.

## Final Value Theorem
If the system is stable, then:
$$
y_{ss} = \lim_{k\to\infty} y(k) = \lim_{z\to 1}(1-z^{-1})Y(z)
$$

## Equivalent Form
Since
$$
1-z^{-1} = \frac{z-1}{z}
$$
another common form is:
$$
y_{ss} = \lim_{z\to 1}\frac{z-1}{z}Y(z)
$$

## Important Condition
- This theorem is only valid when the discrete-time system is stable.
- That means all relevant poles must lie inside the unit circle.

## With a Transfer Function
If
$$
Y(z) = F(z)U(z)
$$
then:
$$
y_{ss} = \lim_{z\to 1}(1-z^{-1})F(z)U(z)
$$

## Scenario
### Scenario
Find the steady-state value of a stable discrete-time system to a unit-step input.

### Given
- Stable pulse transfer function $F(z)$
- Unit-step input:
$$
U(z) = \frac{z}{z-1}
$$

### Steps
1. Write:
$$
Y(z) = F(z)\frac{z}{z-1}
$$
2. Apply the final value theorem:
$$
y_{ss} = \lim_{z\to 1}(1-z^{-1})Y(z)
$$
3. Cancel terms carefully.
4. Evaluate the limit at $z=1$.

### Final Notes
- This is the discrete-time equivalent of the continuous-time final value theorem.
- Always check stability first using [[Discrete-Time Stability]].

## Links
- [[Discrete-Time Stability]]
- [[Discrete-Time System Response]]
- [[Pulse Transfer Functions]]
