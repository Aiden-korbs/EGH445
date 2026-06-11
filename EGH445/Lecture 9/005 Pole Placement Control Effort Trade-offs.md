# Pole Placement Control Effort Trade-offs

## The Trade-off Problem

Pole placement does not consider control effort, ignoring the fundamental trade-off between:

- **Regulating the state** — making $x(kT)$ (or $\delta x(kT)$) small
- **Regulating control effort** — keeping $u(kT)$ small

**Risk:** You might achieve the desired poles but with impractically large control signals, leading to instability — especially on nonlinear systems.

## Example: Nonlinear System

Consider a scalar system with cubic nonlinearity:

$$\dot{x}(t) = -x(t) + x(t)^3 + u(t)$$

- $-x$ represents a stabilizing linear dynamic
- $x^3$ is a destabilizing nonlinearity significant for large $|x|$
- Goal: Stabilise at $\bar{x} = 0$ (requiring $\bar{u} = 0$)

### Step 1: Linearisation

Around $(\bar{x} = 0, \bar{u} = 0)$:

$$A = \frac{\partial}{\partial x}(-x + x^3 + u)\bigg|_{x=0} = (-1 + 3x^2)\bigg|_{x=0} = -1$$
$$B = \frac{\partial}{\partial u}(-x + x^3 + u)\bigg|_{x=0} = 1$$

Linearised continuous-time system:

$$\delta \dot{x}(t) = -\delta x(t) + \delta u(t)$$

### Step 2: Discretisation

With $T = 0.1\,\text{s}$:

$$G = e^{-AT} = e^{0.1} = 0.905$$
$$H = A^{-1}(G - I)B = (-1)^{-1}(0.905 - 1)(1) = 0.095$$

Discrete-time system:

$$x(kT + T) = 0.905x(kT) + 0.095u(kT)$$

### Step 3: Pole Placement Design

Place the closed-loop pole at $p = 0.5$:

$$(G - HK) = 0.905 - 0.095K = 0.5$$
$$0.095K = 0.905 - 0.5 = 0.405$$
$$K = \frac{0.405}{0.095} = 4.263$$

Linear controller:

$$u(kT) = -4.263x(kT)$$

### Step 4: Testing on the Nonlinear System

Simulate the continuous nonlinear dynamics with ZOH (Zero-Order Hold), applying $u(kT)$ constant over $[kT, kT + T)$.

**Result:** The controller derived for the linearised system fails on the nonlinear system. When $|x|$ becomes large, the $x^3$ term dominates and the linear controller cannot stabilise the system.

Simulation output: `Simulation failed at step 2 (t=0.20) for x(0) = 2.4`

## Why It Failed

The linear controller ignores the $x^3$ term, which is only valid for small $x$ near the equilibrium. When $|x|$ becomes large, the nonlinearity dominates and the linear control law is insufficient.

## Key Takeaways

- Pole placement ignores control effort entirely
- Large control gains may work for the linearised model but fail on the actual nonlinear system
- This demonstrates the need for methods that explicitly balance state regulation against control effort — such as optimal control

## Related

- [[003 Pole Placement- When It Works and When It Fails]]
- [[004 Higher-Order and MIMO Pole Placement Limitations]]
- [[006 Optimal Control Fundamentals]]
