# MATLAB Workflow for Digital Control Design

## Purpose
- The lecture includes MATLAB support for:
  - exact discretisation
  - state-space analysis
  - pulse transfer functions
  - pole checking
  - gain verification
  - step and initial condition response

## Common Workflow
### 1. Define the continuous model
Use:
- $A,B,C,D$ for the continuous system

### 2. Convert to discrete form
Typical exact tools shown or implied in the lecture:
- matrix exponential
- exact input matrix integral
- built-in conversion tools

Useful expressions:
$$
G=e^{AT}
$$
$$
H=A^{-1}(G-I)B
$$
for invertible $A$.

### 3. Build the discrete state-space model
Use the sampled matrices and sampling time $T$.

### 4. Check controllability
Construct:
$$
\mathcal{C}_{GH}=\begin{bmatrix}H & GH & \cdots & G^{n-1}H\end{bmatrix}
$$
and check rank.

### 5. Find the gain
- Either:
  - solve coefficient equations manually
  - transform to phase-variable form
  - verify with symbolic algebra

### 6. Analyse response
Useful lecture-referenced functions include:
- `initial`
- `step`
- `stepinfo`
- `evalfr`
- `ss`
- `ss2tf`

## Feedforward Adjustment Workflow
For non-zero reference tracking:
1. form the state-feedback closed-loop system
2. convert it to a transfer function if needed
3. evaluate the steady-state gain at $z=1$
4. compute:
$$
K_r=\frac{K_s}{F_{\text{sf}}(1)}
$$

## Practical Notes
- The lecture recommends checking manual work with MATLAB rather than replacing understanding with software.
- Symbolic tools help when coefficient algebra becomes messy.

## Links
- [[Example 1 - Mass Spring Damper Direct Design]]
- [[Feedforward Gain for Reference Tracking]]
- [[Pole Placement Gain Methods]]

## Visual Placeholders
![[MATLAB Digital Design Workflow.png|400]]
