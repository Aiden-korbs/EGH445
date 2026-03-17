← Back to [[Discrete-time Control System Modelling]]

# Continuous vs Digital Control Architecture

## Continuous Control

- Every signal in the control loop is **continuous-time** and **analogue** — the signal can take an infinite number of values at any given time.
- The controller is implemented using **analogue circuitry** (resistors, capacitors) that can integrate and differentiate signals.
- Transfer function notation: controller $G_C(s)$, plant $G(s)$, sensor $H(s)$.

![[Continuous Control Block Diagram.png|400]]

> **Note:** Strictly speaking, continuous-time signals could also be quantised (specific values only) but still defined at every instant in time.

## Digital Control

- Signals in the loop are a **mixture** of continuous-time, analogue, discrete-time, and digital signals.
- Managed by **A/D** and **D/A** converters, **samplers**, and **Zero Order Holds (ZOH)**.
- The controller is implemented on a **computer/processor** (microcontroller, Raspberry Pi, Pixhawk, etc.) which can only add, subtract, multiply, and divide.

![[Digital Control Block Diagram.png|400]]

## Digital Control Loop Components

| Component | Function |
| :--- | :--- |
| **Sampler** | Acts like a switch — lets a value through at a timed instance (period $T$) |
| **A/D Converter** | Quantises the continuous signal into $Q$ discrete levels |
| **D/A Converter** | Converts digital signal back to analogue |
| **ZOH** | Holds the sampled value constant over the sampling period $T$ |
| **Clock** | Controls and synchronises timing across the loop |

## Signal Notation

| Symbol | Meaning |
| :--- | :--- |
| $k$ | Integer sample index |
| $T = 1/f_s$ | Sampling period |
| $f_s = 1/T$ | Sampling frequency |
| $r(\cdot)$ | Reference input |
| $u(\cdot)$ | Control input |
| $y(\cdot)$ | Plant output |

- Continuous/analogue signals written as $x(t)$
- Discrete/digital signals written as $x(kT)$

> **Notation note:** $x(k)$, $x(kT)$, and $x_k$ are used interchangeably. This course uses $x(kT)$ for consistency with continuous-time notation.

## Related Notes
- [[Discrete Signal Representation]]
- [[Zero Order Hold and Data Hold]]
- [[Sampling Time and Frequency Selection]]
