← Back to [[Week 2 Workshop]]
## Analysing Practical Models

**Scenario** 
Evaluating the system response and stability of complex state-space models, specifically a B747 Aircraft and a Hodgkin-Huxley Neuron, using numerical simulation and Lyapunov functions .

**Given**
* **Model 1:** 
	The 6DOF Aircraft Model linearised around an equilibrium point $\overline{x}$, split into Longitudinal ($\Delta u, \Delta w, \Delta q, \Delta \theta$) and Lateral state matrices .
* **Model 2:** 
	The Hodgkin-Huxley Neuron Model representing membrane potential firing, linearised around an equilibrium point $\overline{x} = [0.5961, 0.0529, 0.3177, 0.0002]^T$ .

**Steps**
1. **Simulate System Response:** 
	Use MATLAB solvers (`initial()`, `lsim()`) to plot the state values over time from a specific initial condition $x_0$ .
2. **Generate Phase Portraits:** 
	Plot states against each other (e.g., Pitch Rate $q$ vs. Pitch Angle $\theta$) on a 2D plane to visualise the trajectory and convergence . 
3. **Evaluate Lyapunov Stability:** 
	 * Define $Q$ as an identity matrix: `Q = eye(4);` 
	 * Solve for $P$ using MATLAB: `P = lyap(A, Q);` 
	 * Calculate energy at each time step $k$: `V(k) = x(k,:) * P * x(k,:)';` 
	 * Plot $V(x)$ over time to visually verify that energy strictly decreases toward zero, confirming asymptotic stability .

**Final Notes**
* The $A$ and $B$ matrices in the aircraft example are highly dependent on specific aircraft construction and environmental conditions (pressure, temperature) .
* Even with highly coupled nonlinear base equations, analyzing the linearized $\tilde{x} = A\tilde{x} + B\tilde{u}$ matrix allows for direct eigenvalue and Lyapunov evaluations .