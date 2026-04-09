# State Feedback Design Procedure

## Standard Workflow
The lecture presents a design process closely matching the continuous-time case.

## Step 1: Check controllability
- Inspect the discrete-time model and test whether it is controllable.
- If not, state feedback cannot arbitrarily move all closed-loop poles.

### Required test
$$
\operatorname{rank}(\mathcal{C}_{GH})=n
$$

## Step 2: Select desired poles
- Choose desired pole locations based on required performance:
  - damping
  - overshoot
  - speed of response
  - stability
- Poles may be chosen in the $s$-plane first and mapped to the $z$-plane.

### Mapping rule
$$
z=e^{sT}
$$

## Step 3: Construct the desired characteristic equation
- Once desired poles $z_1,z_2,\dots,z_n$ are chosen, form:
$$
(z-z_1)(z-z_2)\cdots(z-z_n)=0
$$

## Step 4: Solve for the gain $K$
- Use one of the gain-finding methods:
  - equating coefficients
  - phase-variable form
  - state transformation

## Step 5: Verify the design
- Simulate or analyse:
  - pole locations
  - initial condition response
  - step response
  - steady-state behaviour
- Modify the design if needed.

## Common Warning
- If the system is not fully controllable, some eigenvalues of $G-HK$ cannot be assigned.
- That does **not** automatically mean the system is unstable; uncontrollable modes may already be stable.

## Links
- [[Discrete State Feedback]]
- [[Pole Placement Gain Methods]]
- [[Example 1 - Mass Spring Damper Direct Design]]

## Visual Placeholders
![[State Feedback Design Procedure.png|400]]
