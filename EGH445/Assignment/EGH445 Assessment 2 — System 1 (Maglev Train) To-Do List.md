
---
### **Phase 1: Setup & Understanding**

1. Download the `Train_RealDynamics.zip` file from the assessment page and extract it. Ensure you can open the files in your version of MATLAB/Simulink (check the version compatibility note on the page).
    
2. Read through the provided example `MSD_RealDynamics.zip` carefully — it contains unprotected versions of `System_Dynamics.p` and `System_Simulator.p` and a main script that shows you exactly how to use them. This is your reference for how to structure everything.
    
3. Familiarise yourself with the System 1 equations of motion. Write out all four state equations clearly and identify:
    
    - States: $x_1$ (position, carriage 1), $x_2$ (velocity, carriage 1), $x_3$ (position, carriage 2), $x_4$ (velocity, carriage 2)
    - Input: $u$ (thrust force on carriage 1 only)
    - Outputs: $y_1 = x_2$, $y_2 = x_4$ (velocities only — you cannot measure positions)

---

### **Phase 2: Modelling & Linearisation**

4. Identify a suitable operating point for linearisation. Since the system involves velocity tracking, choose a nominal constant velocity (e.g., some steady-state cruise velocity where accelerations are zero and the coupler is at equilibrium length $L_c = 10$ m).
    
5. Linearise the nonlinear equations of motion about your chosen operating point. This involves computing the Jacobian matrices $A$, $B$, $C$, $D$. Pay special attention to:
    
    - The nonlinear aerodynamic drag term $D_{ai}(x_{2i}) = b_{ai} x_{2i} |x_{2i}|$ (product rule when differentiating)
    - The nonlinear coupling force term $F_{couple}$, which includes the cubic spring term $k_{nl}(x_1 - x_3 - L_c)^3$ (this linearises to zero at equilibrium)
6. Record your nominal parameter values from the table:
    
    - $M_1 = 9000$ kg, $M_2 = 10000$ kg
    - $b_{a1} = 0.5$, $b_{a2} = 0.45$ Ns²/m²
    - $k_c = 5 \times 10^4$ N/m, $d_c = 1 \times 10^5$ Ns/m, $k_{nl} = 1 \times 10^4$ N/m³, $L_c = 10$ m
7. Verify the linearised state-space model $(A, B, C, D)$ is correct by checking dimensions (4 states, 1 input, 2 outputs) and confirming the open-loop eigenvalues make physical sense.
    

---

### **Phase 3: Analysis**

8. Check **controllability** of the $(A, B)$ pair. If not fully controllable, identify which modes are uncontrollable and justify why (physically interpret them).
    
9. Check **observability** of the $(A, C)$ pair. Since only velocities are measured, confirm whether all states (including positions) can be estimated.
    
10. Analyse the open-loop system: plot the poles and zeros, check for stability, and characterise the dynamics (e.g., natural frequencies, damping ratios of the coupling mode).
    

---

### **Phase 4: Controller Design**

11. Choose a controller structure. Since you need output feedback, a natural choice is a **state-feedback controller with a Luenberger observer** (or LQR + observer). Justify your choice in the report.
    
12. Design your **state-feedback gain** $K$ (e.g., pole placement or LQR):
    
    - For pole placement: choose desired closed-loop poles that give fast enough response without excessive control effort. Remember the coupler dynamics — you want the carriages to stay coupled and at relative equilibrium.
    - For LQR: choose weighting matrices $Q$ and $R$, and justify your choices (e.g., penalise velocity error, limit thrust force).
13. Determine what **reference/setpoint** your controller tracks. Since the objective is carriage motion control, define what "controlled motion" means — e.g., tracking a desired velocity profile or a step change in velocity — and augment your system accordingly (e.g., integrator for steady-state tracking).
    

---

### **Phase 5: Observer Design**

14. Design a **Luenberger observer** (or Kalman filter) to estimate all four states from the two velocity measurements ($y_1 = x_2$, $y_2 = x_4$). Choose observer poles that are 3–5× faster than the controller poles.
    
15. Verify that the observer converges correctly in simulation with the linearised model before moving to the black box.
    

---

### **Phase 6: Simulation & Working Model (Assessment 2C)**

16. Implement your complete output-feedback controller (controller + observer combined) in the required format. If using MATLAB, write your `my_controller(t_sample, y_measured)` function that contains all observer update logic and control law computation internally.
    
17. Connect your controller to the **Black Box** (`System_Dynamics.p` / `System_Model_Real.slx`) using `System_Simulator.p` or the Simulink model. Make sure you are only using the measured outputs ($y_1, y_2$) — not the full state.
    
18. Run your baseline simulation and verify the closed-loop system performs as expected (e.g., tracks velocity, coupler force stays bounded).
    
19. Zip your working model files and submit as Assessment 2C by **Week 11**.
    

---

### **Phase 7: Simulation Studies for Demonstration & Report**

20. Design a set of meaningful simulation studies (don't just copy every MSD example plot). Useful studies for System 1 include:
    
    - Step change in desired velocity — does the system track it?
    - Robustness to **parameter uncertainty** (the black box may use different $M_1$, $M_2$, $b_{ai}$ values than nominal)
    - Response to **input disturbances** (e.g., a sudden headwind force)
    - Effect of **output measurement noise** on the observer and control performance
    - Comparing observer estimates vs. true states
    - Coupler force over time — does it remain physically reasonable?
21. Investigate failure modes and performance limits — what happens if you push the reference velocity too high? What if observer gains are too slow or too fast?
    

---

### **Phase 8: Technical Report (Assessment 2B — due Week 13)**

22. Write your report in the specified format (max 6 A4 pages). Structure it to cover:
    - System modelling and linearisation (with your operating point choice justified)
    - Controllability/observability analysis
    - Controller and observer design (with justification of choices and tradeoffs)
    - Simulation results (carefully selected key plots only)
    - Critical analysis of performance, robustness, and limitations

---

### **Phase 9: Demonstration (Assessment 2A — due Week 12)**

23. Prepare your 5–10 minute demonstration. Plan which plots and simulations you'll show — focus on the most insightful ones, not every simulation you ran. Be ready to:
    - Explain your controller and observer design choices
    - Interpret your results physically (what do the plots actually mean for the train?)
    - Answer questions about performance, failure modes, and design tradeoffs

---

**Key dates to keep in mind:**

- Week 11 → Working Model (2C) submission
- Week 12 → Demonstration (2A)
- Week 13 → Technical Report (2B)