← Back to [[Nonlinear Systems and Linearisation]]
## Scenario
Find all equilibrium points of a simple pendulum system and determine their types.

## Given
* System states: $x_1(t) = q(t)$ (angle), $x_2(t) = \dot{q}(t)$ (angular velocity).
* $\dot{x}_1 = x_2$.
* $\dot{x}_2 = -\frac{g}{l}\sin(x_1)$.

## Steps
* Set time derivatives to zero: $f(\overline{x}) = 0$.
* Equation 1: $0 = \overline{x}_2$.
* Equation 2: $0 = -\frac{g}{l}\sin(\overline{x}_1)$.
* The second equation requires $\sin(\overline{x}_1) = 0$, which occurs at integer multiples of $\pi$.

## Final Notes
* The formal solution is $\overline{x}_1^k = \pm k\pi$ and $\overline{x}_2^k = 0$, where $k \in \mathbb{Z}$.
* The system is nonlinear.
* The pendulum exhibits **infinite** and **isolated** equilibrium points (pointing straight up or straight down).