← Back to [[Week 1 Workshop]]

## State-Space Linearisation

**Scenario** Converting the complex equations from [[6DOF Aircraft Nonlinear Equations]] into decoupled linear state-space models for control application . 

**Given**
* Variables with $\Delta$ denote small perturbations from an equilibrium point (linearisation) .

**Steps**
* **Longitudinal Dynamics:** Captures forward motion and pitch . 
* The state vector is defined as $[\Delta u, \Delta w, \Delta q, \Delta\theta]^T$ .
	* Matrix Equation: $$\begin{bmatrix} \Delta\dot{u} \\ \Delta\dot{w} \\ \Delta\dot{q} \\ \Delta\dot{\theta} \end{bmatrix} = \begin{bmatrix} X_u & X_w & 0 & -g\cos\theta_0 \\ \frac{Z_u}{1-Z_{\dot{w}}} & \frac{Z_w}{1-Z_{\dot{w}}} & \frac{u_0+Z_q}{1-Z_{\dot{w}}} & -\frac{g\sin\theta_0}{1-Z_{\dot{w}}} \\ A & B & C & D \\ 0 & 0 & 1 & 0 \end{bmatrix} \begin{bmatrix} \Delta u \\ \Delta w \\ \Delta q \\ \Delta\theta \end{bmatrix} + \dots$$
* **Lateral Dynamics:** Captures side-to-side motion, roll, and yaw . The state vector is defined as $[\Delta v, \Delta p, \Delta r, \Delta\phi]^T$ .
	* Matrix Equation: $$\begin{bmatrix} \Delta\dot{v} \\ \Delta\dot{p} \\ \Delta\dot{r} \\ \Delta\dot{\phi} \end{bmatrix} = \begin{bmatrix} Y_v & Y_p & -(u_0-Y_r) & g\cos\theta_0 \\ \frac{L'_v}{I'} + I''I_z N_v & \frac{L'_p}{I'} + I''I_z N_p & \frac{L'_r}{I'} + I''I_z N_r & 0 \\ \dots & \dots & \dots & \dots \end{bmatrix} \begin{bmatrix} \Delta v \\ \Delta p \\ \Delta r \\ \Delta\phi \end{bmatrix} + \dots$$
	
**Final Notes**
* Constants such as $I'$ and $I''$ simplify the cross-coupling inertia terms: $I' = 1 - \frac{I_{xz}^2}{I_x I_z}$ and $I'' = \frac{I_{xz}}{I_x I_z I'}$ .