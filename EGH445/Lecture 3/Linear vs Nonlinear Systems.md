← Back to [[Nonlinear Systems and Linearisation]]
## Linear Systems
* **Definition**: A system $G$ is linear with respect to its inputs $u$ and output $y$ if and only if **superposition** holds.
	* Superposition requires both **additivity** ($G(u_1 + u_2) = G(u_1) + G(u_2)$) and **homogeneity** ($G(\alpha u_1) = \alpha G(u_1)$).
	* Linear systems possess analytical, closed-form solutions.
	* Stability can often be determined globally depending on the dynamics.

## Nonlinear Systems
* **Definition**: Systems where superposition does not hold. 
	* Nonlinearities can occur inherently (e.g., backlash, hysteresis) or mathematically via trigonometric functions, absolute values, or state multiplications.
	* Solutions are generally numerical approximations rather than analytical.
	* Stability is typically determined locally.

## Time-Variance
Systems (both linear and nonlinear) can be categorised by their relationship to time:
* **Time-Invariant**: The relationship between input $u(t)$ and output $y(t)$ is constant with respect to time $t$.Matrices or functions do not explicitly depend on $t$.
* **Time-Varying**: System dynamics change over time, requiring models with explicit time dependencies like $A(t)$ or $f(t, x(t), u(t))$.