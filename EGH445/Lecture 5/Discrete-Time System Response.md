# Discrete-Time System Response

## Main Idea
- Discrete-time system response can be found in ways very similar to continuous-time systems.
- Response can be computed from:
  - the **pulse transfer function**
  - the **discrete state-space model**
  - a **difference equation**
  - **recursion**
  - the **inverse $\mathcal{Z}$ transform**

## Common Paths
| Method | Starting Point | Typical Use |
|---|---|---|
| Transfer-function method | $F(z)$ and input $U(z)$ | Direct algebra in the $z$-domain |
| Inverse $\mathcal{Z}$ transform | $Y(z)$ | Closed-form sequence |
| State recursion | $x(k+1)=Gx(k)+Hu(k)$ | Step-by-step simulation |
| Difference equation | Output-input relation | Direct sequence update |

## Transfer-Function Route
- Compute:
$$
Y(z) = F(z)U(z)
$$
- Then take the inverse $\mathcal{Z}$ transform to get:
$$
y(k)
$$

## State-Space Route
- Use:
$$
x(k+1) = Gx(k) + Hu(k)
$$
$$
y(k) = Cx(k) + Du(k)
$$
- Repeatedly update the state to generate the response.

## Recursion View
- The response at each sample depends on:
  - previous states or outputs
  - current and possibly previous inputs

## Why It Matters
- This gives direct access to:
  - step response
  - transient behavior
  - sampled output values
  - comparison with continuous-time response

## Scenario
### Scenario
Find the sampled response of a stable discrete-time plant to a unit-step input.

### Given
- Discrete transfer function $F(z)$
- Unit-step input sequence $u(k)=1$
- Zero initial conditions

### Steps
1. Compute:
$$
U(z) = \frac{z}{z-1}
$$
2. Form:
$$
Y(z) = F(z)U(z)
$$
3. Simplify using partial fractions or transform tables.
4. Apply the inverse $\mathcal{Z}$ transform.
5. Interpret $y(k)$ sample-by-sample.

### Final Notes
- This method mirrors continuous-time response work, but uses sampled sequences and the $z$-domain.

## Links
- [[Pulse Transfer Functions]]
- [[Discrete Final Value]]
- [[Discrete Transfer Function from State Space]]

## Visuals
![[Discrete Response Workflow.png|400]]
