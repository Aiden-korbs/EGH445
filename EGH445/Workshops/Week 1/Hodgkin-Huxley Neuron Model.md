← Back to [[Week 1 Workshop]]

## Modelling Biological Systems

**Scenario** 
Creating a control model for a biological system, specifically representing a neuron membrane using electrical circuit equivalents .

**Given**
* A neuron with an intracellular cytoplasm and an extracellular side .
* Three primary ionic channels: Sodium (Na), Potassium (K), and a Leak channel .
* The system output is the membrane voltage, denoted as $V_m$ .

**Steps**
1. **Identify Circuit Components:**
	![[HodgkinHuxley_Circuit.png|400]]
   * Conductances are denoted by $G_{Na}$, $G_K$, and $G_l$ .
   * Reversal potentials are denoted by $E_{Na}$, $E_K$, and $E_l$ .
   * The membrane has a capacitance $C$ .
1. **Define the Ionic Current Equation:** The total ionic current $I$ contains linear and nonlinear terms . $$I = C\dot{V}_m + G_K n^4 (V_m - E_K) + G_{Na} m^3 h(V_m - E_{Na}) + G_l(V_m - E_l)$$ 
**Final Notes**
* The variables $n$, $m$, and $h$ in the current equation represent non-linear "activation gates", which require their own differential equations mapped in [[Hodgkin-Huxley Activation Gates]] .