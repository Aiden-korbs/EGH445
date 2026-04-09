# Aircraft Controllability and Observability Check

## Goal
- Before controller design, the workshop checks whether the aircraft model is:
  - **controllable**
  - **observable**

## Output Matrix
- The workshop states:
$$
C = \begin{bmatrix} 1 & 0 & 0 & 1 \end{bmatrix}
$$
- Interpreted in the slides as measuring:
  - **pitch angle**
  - **forward velocity**

## Controllability Matrix
$$
\mathcal{C}_{GH} = \begin{bmatrix} H & GH & G^2H & \cdots & G^{n-1}H \end{bmatrix}
$$

## Observability Matrix
$$
\mathcal{O}_{GC} = \begin{bmatrix}
C^T & (CG)^T & (CG^2)^T & \cdots & (CG^{n-1})^T
\end{bmatrix}^T
$$

## Workshop Result
- MATLAB output in the slide reports:
  - controllability matrix rank $= 4$
  - observability matrix rank $= 4$

## Conclusion
- Because the system order is $4$, rank $4$ means the model is:
  - **controllable**
  - **observable**

## Why This Matters
- A controllable aircraft model supports **state feedback design**.
- An observable aircraft model supports **state reconstruction/observer design** if needed.

## Scenario
### Scenario
Verify whether the discretised aircraft model can support state-feedback design.

### Given
- System order:
$$
n = 4
$$
- Rank of controllability matrix:
$$
\operatorname{rank}(\mathcal{C}_{GH}) = 4
$$
- Rank of observability matrix:
$$
\operatorname{rank}(\mathcal{O}_{GC}) = 4
$$

### Steps
1. Compare each matrix rank to the system order $n$.
2. Check whether:
$$
\operatorname{rank}(\mathcal{C}_{GH}) = n
$$
3. Check whether:
$$
\operatorname{rank}(\mathcal{O}_{GC}) = n
$$
4. Conclude whether both properties hold.

### Final Notes
- Since both ranks equal $4$, the discretised aircraft model is suitable for the state-feedback workflow shown in the workshop.

## Links
- [[Controllability and Observability Workshop View]]
- [[Aircraft Performance Objectives]]
- [[Aircraft State Feedback Design]]

## Visual Placeholders
![[Aircraft CTRB OBSV Check.png|400]]
