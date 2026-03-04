← Back to [[Week 2 Workshop]]

## BIBO vs. Internal Stability 
Stability dictates whether a system's response remains bounded or decays to zero over time .

### BIBO Stability (External)
* **Definition:** A linear time-invariant (LTI) system is Bounded-Input-Bounded-Output (BIBO) stable if every bounded input $u(t)$ produces a bounded output $y(t)$ .
* **Condition:** The transfer function $H(s)$ is BIBO stable if and only if all of its poles have negative real parts .

### Internal Stability
* **Definition:** An unforced, homogeneous LTI system ($\dot{x}(t) = Ax(t)$) is internally stable if, for every initial condition, all internal states decay to zero .
$$||x|| \rightarrow 0 \text{ as } t \rightarrow \infty$$ 
* **Condition:** The system is internally stable if and only if the real parts of **all** eigenvalues of matrix $A$ are negative .
* **Relationship:** Internal stability is a "stronger" condition than BIBO stability . Internal stability guarantees BIBO stability, but a system can be BIBO stable while having unstable internal states (e.g., due to pole-zero cancellation) .