# Feedforward Gain for Reference Tracking

## Purpose
- The feedforward gain $K_r$ is used with state feedback so the discrete system can track a **fixed non-zero reference**.

## Why It Is Needed
- Pole placement via $K$ changes the closed-loop poles, but it can also change the steady-state gain.
- As a result, the output may settle to the wrong constant value even if the transient response looks good.

## Control Law
$$
u(kT)=K_r\,r(kT)-Kx(kT)
$$

## Closed-Loop Model
$$
x(kT+T)=(G-HK)x(kT)+HK_r\,r(kT)
$$

## Steady-State Matching Idea
The lecture extension compares:
- the **continuous-time closed-loop steady-state value**
- the **discrete-time closed-loop steady-state value**

Then $K_r$ is selected so these steady-state values match.

## Transfer-Function View
If the discrete closed-loop transfer function without feedforward is $F_{\text{sf}}(z)$, then a practical computation is:
$$
K_r=\frac{K_s}{F_{\text{sf}}(1)}
$$
where:
- $K_s$ is the desired continuous-time steady-state gain
- $F_{\text{sf}}(1)$ is the discrete closed-loop gain evaluated at $z=1$

## Final-Value Logic
- Evaluating at:
$$
z=1
$$
is tied to the discrete final value theorem for stable systems.

## Scenario
### Scenario
Adjust a discrete state-feedback design so that a step reference is tracked with the correct steady-state value.

### Given
- A stable closed-loop discrete system
- A state-feedback gain $K$
- A desired steady-state gain from the continuous design or reference requirement

### Steps
1. Form the discrete closed-loop system with state feedback only.
2. Find its transfer function from reference to output.
3. Evaluate the steady-state gain at $z=1$.
4. Compare with the desired steady-state value.
5. Choose $K_r$ to correct the mismatch.

### Final Notes
- $K$ shapes pole locations and transients.
- $K_r$ fixes the constant-reference tracking level.

## Links
- [[Regulation with Non-Zero Reference]]
- [[Discrete State Feedback]]
- [[MATLAB Workflow for Digital Control Design]]
