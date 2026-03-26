# Aliasing and Nyquist Criterion

## Definition
- **Aliasing** occurs when a signal is sampled too slowly, causing different continuous-time frequencies to produce the same sampled sequence.
- The system may then reconstruct the **wrong signal** from the samples.

## Nyquist Criterion
- To reconstruct a signal unambiguously, the highest signal frequency $f$ must satisfy:
$$
f < \frac{f_s}{2}
$$
- The quantity
$$
\frac{f_s}{2}
$$
is the **Nyquist rate**.

## Alias Frequencies
- Reconstructed frequencies can appear as:
$$
\hat{f} = |f \pm n f_s|,\quad n \in \{1,2,\dots\}
$$
- This means a high-frequency signal can appear as a lower-frequency one after sampling.

## Interpretation
- If $f > \frac{f_s}{2}$:
  - the original signal cannot be identified uniquely
  - lower-frequency aliases may appear
- If $f = \frac{f_s}{2}$:
  - the signal is at the Nyquist limit
  - ambiguity still exists in reconstruction
- If $f < \frac{f_s}{2}$:
  - no lower-frequency alias appears
  - but higher-frequency candidates can still map to the same samples

## Example Cases
| Original Frequency | Sampling Frequency | Outcome |
|---|---|---|
| $f = 25\text{ Hz}$ | $f_s = 20\text{ Hz}$ | Aliasing occurs because $25 > 10$ |
| $f = 25\text{ Hz}$ | $f_s = 50\text{ Hz}$ | At Nyquist limit |
| $f = 25\text{ Hz}$ | $f_s = 100\text{ Hz}$ | Correct low-frequency reconstruction |

## Why This Matters in Control
- Aliasing can make the controller:
  - track the wrong reference
  - respond to false output behavior
  - misinterpret noise as low-frequency dynamics

## Links
- [[Sampling Time Selection]]
- [[Tracking Effectiveness in Digital Control]]
- [[Regulation Effectiveness and Anti-Alias Filtering]]
- [[s-Plane to z-Plane Mapping]]

## Visuals
![[Aliasing Example 20Hz Sampling.png|400]]
![[Aliasing Example 50Hz Sampling.png|400]]
![[Aliasing Example 100Hz Sampling.png|400]]
