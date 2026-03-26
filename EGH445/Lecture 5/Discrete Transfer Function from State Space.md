# Discrete Transfer Function from State Space

## Discrete State-Space Model
A discrete-time state-space model has the form:
$$
x(kT+T) = Gx(kT) + Hu(kT)
$$
$$
y(kT) = Cx(kT) + Du(kT)
$$

## Goal
- Find the pulse transfer function:
$$
F(z) = \frac{Y(z)}{U(z)}
$$

## Apply the Z Transform
Applying the unilateral $\mathcal{Z}$ transform gives:
$$
zX(z) - zx(0) = GX(z) + HU(z)
$$
$$
Y(z) = CX(z) + DU(z)
$$

## Zero Initial Conditions
- For transfer function derivation, assume:
$$
x(0) = 0
$$

Then:
$$
zX(z) = GX(z) + HU(z)
$$

Rearrange:
$$
(zI - G)X(z) = HU(z)
$$

So:
$$
X(z) = (zI - G)^{-1}HU(z)
$$

Substitute into the output equation:
$$
Y(z) = C(zI-G)^{-1}HU(z) + DU(z)
$$

Hence:
$$
F(z) = \frac{Y(z)}{U(z)} = C(zI-G)^{-1}H + D
$$

## Expanded Matrix Form
- Another common form is:
$$
F(z) = \frac{C\,\mathrm{adj}(zI-G)\,H}{\det(zI-G)} + D
$$

## Pole Condition
- The poles are determined by:
$$
\det(zI-G) = 0
$$

## Similarity Transform Note
- Different state definitions do not change the poles.
- Under a similarity transform:
$$
x(k) = P\bar{x}(k)
$$
the pole locations are unchanged.

## Links
- [[Pulse Transfer Functions]]
- [[Discrete-Time Stability]]
- [[Discrete-Time System Response]]

## Visuals
![[Discrete State Space to Transfer Function.png|400]]
