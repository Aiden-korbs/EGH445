# Pole Placement: When It Works and When It Fails

## When Pole Placement Works Well

Pole placement is effective for:

- **SISO systems** (Single Input Single Output)
- **Low-order systems** (2nd order or when a 2nd-order dominant approximation is valid)

In these cases, the mapping between pole locations and time-domain response is intuitive, and the design is unique.

## When Pole Placement Fails

Pole placement performs poorly for:

- **Higher-order systems** ($n \geq 4$)
- **MIMO systems** (Multiple Input Multiple Output)
- **Stiff systems** (e.g., with widely separated time constants like 1 ms and 1 s)
- **Highly nonlinear systems** (linearisation quickly becomes invalid away from the operating point)

## Why Pole Placement Breaks Down

### Higher-Order Systems

For $n > 3$, the link between pole locations and the desired time-domain response becomes unclear. Arbitrary pole choices can lead to:

- Poor performance
- Excessive control effort
- Unstable behaviour when applied to the nonlinear system

### MIMO Systems

For MIMO systems with $x(kT) \in \mathbb{R}^n$, $u(kT) \in \mathbb{R}^m$, $y(kT) \in \mathbb{R}^p$ ($n, m, p > 1$):

- Specifying only the eigenvalues leaves degrees of freedom in the eigenvectors
- The eigenvectors directly affect the system response
- The design process becomes non-unique and less intuitive
- Handling interactions between inputs and outputs requires additional considerations

### Control Effort

Pole placement does not consider control effort. You might achieve the desired poles but with impractically large control signals, which can lead to instability — especially when applied to nonlinear systems.

## Key Takeaways

| System Type | Pole Placement Suitable? | Reason |
|---|---|---|
| SISO, low-order | Yes | Intuitive pole-to-response mapping |
| SISO, higher-order | No | No clear design guidelines for $n > 3$ |
| MIMO | No | Degrees of freedom in eigenvectors; non-unique |
| Stiff | No | Widely separated dynamics complicate pole selection |
| Highly nonlinear | No | Linearisation invalid away from operating point |

## Related

- [[004 Higher-Order and MIMO Pole Placement Limitations]]
- [[005 Pole Placement Control Effort Trade-offs]]
- [[006 Optimal Control Fundamentals]]
