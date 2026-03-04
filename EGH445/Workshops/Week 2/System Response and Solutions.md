← Back to [[Week 2 Workshop]]

## Solving State-Space Models 
To understand how a system behaves after time $t_0$, we must solve the state-space equation $\dot{x} = f(x,u)$ given an input $u(t)$ and an initial condition $x(t_0) = x_0$ . 

### Numerical Integration (Nonlinear Systems) 
For nonlinear systems, solutions are found using numerical simulation (ODE integration) .
* **Iterative Process:** The state at the next time step is found by integrating over a small time window $h$: $$x(t_{n+1}) = x(t_n) + \int_{t_n}^{t_{n+1}} f(x,u)dt$$ 
* **Solvers:** Methods like forward/backward Euler or Heun-Euler (trapezoidal) are used to approximate the integral . MATLAB provides various ODE solvers depending on system stiffness .

### Analytical Solution (Linear Systems) 
For linear time-invariant (LTI) systems defined by $\dot{x} = Ax + Bu$, an exact analytical formula exists .
* **General Solution:** The response is a combination of the homogeneous (unforced) solution and the particular (forced) solution : $$x(t) = e^{At}x_0 + \int_{0}^{t} e^{A(t-\tau)}Bu(\tau)d\tau$$ 
* **State Transition Matrix ($e^{At}$):** The matrix exponential $e^{At}$ governs the natural unforced transition of the states . It can be found via inverse Laplace transform: $$e^{At} = \mathcal{L}^{-1}\{(sI - A)^{-1}\}$$ 