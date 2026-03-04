← Back to [[Week 1 Workshop]]

## Activation Gate State-Space Equations

**Scenario** 
Defining the nonlinear state-space model that governs the behavior of the ionic activation gates inside the [[Hodgkin-Huxley Neuron Model]] .

**Given**
* The system relies on three states defined as 'activation gates' .
* **Sodium gate:** $n$ .
* **Potassium gate:** $m$ .
* **Leak gate:** $h$ .

**Steps**
1. **Define the State Derivatives:** Each gate's rate of change is dependent on nonlinear functions $\alpha_x$ and $\beta_x$, where $x \in \{n, m, h\}$ . $$\dot{n} = \alpha_n(V_m)(1 - n) - \beta_n(V_m)n$$  $$\dot{m} = \alpha_m(V_m)(1 - m) - \beta_m(V_m)m$$  $$\dot{h} = \alpha_h(V_m)(1 - h) - \beta_h(V_m)h$$
2. **Define the Nonlinear Coefficients ($\alpha_x$, $\beta_x$):**
   * **For $n$:** $$\alpha_n(V_m) = \frac{0.01(10 - V_m)}{\exp(\frac{10 - V_m}{10}) - 1}$$  $$\beta_n(V_m) = 0.125 \exp(-\frac{V_m}{80})$$ * **For $m$:** $$\alpha_m(V_m) = \frac{0.1(25 - V_m)}{\exp(\frac{25 - V_m}{10}) - 1}$$  $$\beta_m(V_m) = 4 \exp(-\frac{V_m}{18})$$ * **For $h$:** $$\alpha_h(V_m) = 0.07 \exp(-\frac{V_m}{20})$$  $$\beta_h(V_m) = \frac{1}{\exp(\frac{30 - V_m}{10}) + 1}$$ 
**Final Notes**
* Because $\alpha$ and $\beta$ are fundamentally dependent on the membrane voltage ($V_m$), these equations form a highly coupled, nonlinear state-space model representing the biological system .