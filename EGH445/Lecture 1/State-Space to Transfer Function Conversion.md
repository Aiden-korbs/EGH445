Links to [[Model Conversions]]

 Overview State-space models can be converted into **Transfer Functions** to analyze the input-output relationship in the frequency domain . This conversion relies on the **Laplace transform** and matrix algebra, specifically accounting for the fact that matrices do not generally commute .

## Mathematical Representation The relationship between the models is defined by the following equations :

| State-Space Model | Transfer Function Model |
| :--- | :--- |
| $\begin{cases} \dot{x} = Ax + Bu \\ y = Cx + Du \end{cases}$ | $H(s) = \frac{Y(s)}{U(s)} = C(sI - A)^{-1}B + D$ |

## Derivation
### Scenario Converting a linear time-invariant (LTI) system from state-space form to a transfer function .

### Given
* State equation: $\dot{x} = Ax + Bu$ .
* Output equation: $y = Cx + Du$ .
* Identity matrix $I = \begin{bmatrix} 1 & 0 & \dots & 0 \\ \vdots & \ddots & & \vdots \\ 0 & 0 & \dots & 1 \end{bmatrix}$ .

### Steps
1. **Apply Laplace Transform**: Transform the time-domain equations into the $s$-domain, assuming zero initial conditions ($x(0)=0$) :
   $$sX(s) = AX(s) + BU(s)$$
   $$Y(s) = CX(s) + DU(s)$$
2. **Isolate State Vector**: Rearrange the state equation to group $X(s)$ terms :
   $$sX(s) - AX(s) = BU(s)$$
   $$(sI - A)X(s) = BU(s)$$
3. **Solve for $X(s)$**: Multiply both sides by the inverse matrix $(sI - A)^{-1}$. Note that order matters as matrices do not commute :
   $$(sI - A)^{-1}(sI - A)X(s) = (sI - A)^{-1}BU(s)$$
   $$X(s) = (sI - A)^{-1}BU(s)$$
4. **Substitute into Output Equation**: Insert the expression for $X(s)$ into the transformed output equation :
   $$Y(s) = C[(sI - A)^{-1}BU(s)] + DU(s)$$
5. **Factor out Input**: Extract $U(s)$ to find the transfer function $H(s)$ :
   $$Y(s) = [C(sI - A)^{-1}B + D]U(s)$$


### Final Notes
The term $(sI - A)^{-1}$ is central to the system's dynamics. The roots of the denominator, $\det(sI - A) = 0$, define the **poles** of the system, which are identical to the **eigenvalues** of the state matrix $A$ .
