← Back to [[Response and Stability]]

## Numerical Simulation for Nonlinear Systems 
When analytical solutions are impossible, numerical integration steps through time to approximate the state $x(t)$.

### The Iterative Process 
Given a step size $h$ where $t_n = t_0 + nh$ , the solution is found iteratively: $$x(t_{n+1}) = x(t_n) + \int_{t_n}^{t_{n+1}} f(x,u)dt$$  MATLAB and Simulink use different solvers to approximate this integral.

### Fixed Step Methods
* **Euler (Forward) Method:** Uses a simple rectangular approximation of the integral. $$x_{t_{n+1}} = x_{t_n} + h f(x_{t_n}, u_{t_n})$$ 
* **Heun-Euler Method:** Uses a trapezoidal approximation for better accuracy. $$x_{t_{n+1}} = x_{t_n} + \frac{h}{2}(f(x_{t_n}, u_{t_n}) + f(x_{t_{n+1}}, u_{t_{n+1}}))$$ 
### Dealing with Stiff Systems 
* A system is "stiff" when it has both very fast and very slow dynamics.
* Fast dynamics (eigenvalues far from the imaginary axis) require a very small time step $h$ to accurately capture the transient response.
* Slow dynamics (eigenvalues close to the imaginary axis) require a long simulation time to see the system settle.
* Specialised stiff ODE solvers are required to efficiently handle these competing requirements.