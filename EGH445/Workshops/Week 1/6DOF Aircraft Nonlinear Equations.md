← Back to [[Week 1 Workshop]]

## Nonlinear Dynamics of a 6DOF Aircraft

**Scenario** Establishing the foundational nonlinear equations of motion for an aircraft before attempting to linearise them for control design .

**Given**
* A system using the standard variables defined in [[6DOF Aircraft Model Variables]] .
* Forces in the system are denoted by $X$, $Y$, and $Z$ .
* Moments in the system are denoted by $L'$, $M$, and $N$ .

**Steps**
1. **Define Force Equations:** $$X + T \cos \alpha_T - mg \sin \theta = m(\dot{u} + qw - rv)$$  $$Y + mg \cos \theta \sin \phi = m(\dot{v} - pw + ru)$$  $$Z + T \sin \alpha_T + mg \cos \theta \cos \phi = m(\dot{w} + pv - qu)$$ 2. **Define Moment Equations:** $$L' = I_x \dot{p} - I_{xz} \dot{r} - q(I_{xz} p - I_z r) - I_y qr$$  $$M = I_y \dot{q} + p(I_{xz} p - I_z r) + r(I_x p - I_{xz} r)$$  $$N = I_z \dot{r} - I_{xz} \dot{p} - q(I_x p - I_{xz} r) + I_y pq$$ 3. **Define Kinematics:** $$\dot{\phi} = p + (q \sin \phi + r \cos \phi) \tan \theta$$  $$\dot{\theta} = q \cos \phi - r \sin \phi$$  $$\dot{\psi} = (q \sin \phi + r \cos \phi) \sec \theta$$ 
**Final Notes**
* These equations are strictly for foundational understanding and motivation; full memorisation is not required for the workshop .