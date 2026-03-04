## Basic Configurations
| Type | Diagram Placeholder | Transfer Function |
| :--- | :--- | :--- |
| **Series** | ![[Series Block.png]] |$G_2 G_1$ |
| **Parallel** | ![[Parallel Block.png]] |$G_2 + G_1$ |
| **Feedback** | ![[Feedback Block.png]] |$\frac{G_1}{1 + G_2 G_1}$ |

## State-Space RepresentationState-space models can be visualized using integrators ($\int$), gains, and summing junctions.

### Matrix Form Block Diagram
![[Matrix Form Diagram.png|500]]
*Path through $B$ and Integrator defines $\dot{x}$.
*Feedback loop through $A$ represents internal dynamics.
*Path through $C$ and summing junction $D$ defines $y$.

### Component FormFor a 2nd order system:$$\dot{x}_1 = a_{11}x_1 + a_{12}x_2 + b_1u$$
*This is visualized by two separate integrator paths connected by cross-coupling gains ($a_{12}, a_{21}$).