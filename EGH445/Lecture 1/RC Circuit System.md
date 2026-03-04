## Scenario 
A simple electrical circuit with a resistor ($R$) and a capacitor ($C$) connected to a voltage source $V$
## Given
*$V = V_R + V_C$
$V_R = Ri$
$i = C\frac{dV_C}{dt}$

## Steps
1. **Model Dynamics**:
	*$V = RC\dot{V}_C + V_C$
	$\dot{V}_C = -\frac{1}{RC}V_C + \frac{1}{RC}V$
2. **Define State**:
	* Let $x = V_C$. Then $\dot{x} = [-\frac{1}{RC}]x + [\frac{1}{RC}]u$.
3. **Alternative State**:
	* Let $x = q(t) = CV_C$. Then $\dot{x} = [-\frac{1}{RC}]x + [\frac{1}{R}]u$.

## Final Notes
States are **not unique**; different physical quantities (voltage vs. charge) can be chosen to represent the same system dynamics.

![[RC Circuit Scope.png|400]]