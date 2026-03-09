← Back to [[Nonlinear Systems and Linearisation]]
## Hartman & Grobman Theorem
* **Definition**: If the Jacobian matrix $A$ has no eigenvalues with a zero real part, then the trajectories of the linearised system will closely resemble those of the true nonlinear system near the equilibrium point.

## Eigenvalue Classifications
* The types of equilibrium points in a 2D phase portrait dictate the localised response of the system based on its eigenvalues:

| Eigenvalues of A                | Type of Equilibrium Point | Stability                     |
| :------------------------------ | :------------------------ | :---------------------------- |
| $\lambda_2 < \lambda_1 < 0$     | Stable Node               | Stable                        |
| $\lambda_2 > \lambda_1 > 0$     | Unstable Node             | Unstable                      |
| $\lambda_2 < 0 < \lambda_1$     | Saddle                    | Unstable                      |
| $\alpha \pm j\beta, \alpha < 0$ | Stable Focus              | Stable                        |
| $\alpha \pm j\beta, \alpha > 0$ | Unstable Focus            | Unstable                      |
| $\alpha \pm j\beta, \alpha = 0$ | Center                    | Neutral (Linearization Fails) |

![[Phase_Portraits.png]]