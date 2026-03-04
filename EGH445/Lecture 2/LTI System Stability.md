← Back to [[Response and Stability ]]

## Stability Classifications
Stability analysis determines if a system's output or internal states will remain bounded or decay over time.

### BIBO Stability (External)
* **Definition:** 
	A system is Bounded-Input-Bounded-Output (BIBO) stable if every bounded input $u(t)$ results in a bounded output $y(t)$.
* **Condition:** 
	The system is BIBO stable if, and only if, all poles of its transfer function $H(s)$ have negative real parts.

### Internal Stability
* **Definition:** 
	A homogeneous LTI system ($\dot{x} = Ax$) is internally stable if, for every initial condition $x(0)$, all internal states decay to zero ($||x|| \rightarrow 0$ as $t \rightarrow \infty$).
* **Condition:** 
	The system is internally stable if, and only if, the real parts of **all** eigenvalues of matrix $A$ are strictly negative.

### The Relationship
Internal stability is a stronger condition than BIBO stability.If $\dot{x} = Ax$ is internally stable (all eigenvalues have negative real parts), the system is guaranteed to be BIBO stable.However, a system can be BIBO stable while having unstable internal states due to pole-zero cancellations.