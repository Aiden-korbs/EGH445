# Mass-Spring-Damper Design 2 Example

## System Definition
- The lecture uses a mass-spring-damper example with states:
$$
x_1 \equiv y,\qquad x_2 \equiv v,\qquad u \equiv F
$$

## Continuous-Time Model
For one example:
$$
\dot{x} =
\begin{bmatrix}
0 & 1\\
-\frac{k}{m} & -\frac{b}{m}
\end{bmatrix}x
+
\begin{bmatrix}
0\\
\frac{1}{m}
\end{bmatrix}u
$$
$$
y = \begin{bmatrix}1 & 0\end{bmatrix}x
$$

## Discrete Example
One discretised model shown in the lecture is:
$$
x(kT+T)=
\begin{bmatrix}
0.9952 & 0.0950\\
-0.0950 & 0.9002
\end{bmatrix}
x(kT)
+
\begin{bmatrix}
0.0048\\
0.0950
\end{bmatrix}u(kT)
$$
$$
y(kT)=\begin{bmatrix}1 & 0\end{bmatrix}x(kT)
$$

## Lecture Lessons from This Example
- Pure state feedback stabilises the system.
- Constant disturbance causes steady-state offset.
- Feedforward can cancel known disturbance but is fragile to model mismatch.
- Integral action rejects constant disturbance and achieves zero steady-state error.
- Sinusoidal tracking needs a richer internal model than a single integrator.

## Scenario
### Scenario
Compare disturbance rejection methods on a mass-spring-damper plant with model mismatch.

### Given
- Nominal controller designed with $\hat{m}=1$
- Actual plant mass may be
$$
m = 1.1
$$
- Constant disturbance:
$$
d(kT)=1
$$

### Steps
1. Design state feedback on the nominal plant.
2. Test with disturbance only.
3. Add feedforward cancellation and observe sensitivity to mismatch.
4. Add integral action via augmentation.
5. Compare steady-state output error and transient shape.

### Final Notes
- The example shows why structural robustness matters more than exact cancellation.

## Links
- [[Feedforward Disturbance Compensation]]
- [[Integral Action for Disturbance Rejection]]
- [[Sinusoidal Tracking by Augmentation]]

## Visual Placeholders
![[Mass Spring Damper with Disturbance.png|400]]
