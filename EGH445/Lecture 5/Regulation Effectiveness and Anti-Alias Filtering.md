# Regulation Effectiveness and Anti-Alias Filtering

## Key Idea
- In discrete-time systems, **high-frequency noise** is much more dangerous because sampling can alias it into lower frequencies.
- The controller can then respond to a **false output signal**.

## Noise Sources
- Noise may come from:
  - actuator input disturbances
  - sensor noise
  - unmodelled plant disturbances

## Output with Noise
- The measured signal can be written as:
$$
y_m(t) = y(t) + w(t)
$$
where $w(t)$ is additive noise.

## Problem
- Even if the plant output $y(t)$ is acceptable, the sampled output $y(k)$ may be corrupted by aliased noise.
- This distorts:
  - the reconstructed signal shape
  - the error signal
  - controller behavior

## Example Signal Model
- A noisy signal can be represented as:
$$
x(t) = x_1(t) + x_2(t) + w(t)
$$
- Example components:
$$
x_1(t) = \cos(2\pi f_1 t),\qquad x_2(t) = \sin(2\pi f_2 t)
$$
$$
w(t) = A\cos(2\pi f_w t)
$$

## Why Faster Sampling Alone Is Not Enough
- If the noise frequency $f_w$ is very high, then avoiding noise aliasing requires:
$$
f_s > 2f_w
$$
- This may be impractical.

## Anti-Alias Filter
- Solution: add a **low-pass analogue filter** before the sampler.
- Typical form:
$$
H_f(s) = \frac{a}{s+a}
$$
where $a$ is the filter breakpoint or cutoff-related parameter.

## Purpose of the Filter
- Remove high-frequency noise **before** it is sampled.
- Allow lower practical sampling rates.
- Prevent noise from entering digital components.

## Trade-Off
- The filter also adds **lag**.
- That lag can affect:
  - performance
  - stability
  - controller design

## Filter Design Options
### Option 1: Strong filtering, more lag
- Choose:
$$
a \ll 10f
$$
- Effect:
  - good noise reduction
  - significant lag
  - filter must be included in the plant model
  - extra compensation may be needed

### Option 2: Minimal lag, high sample rate
- Choose:
$$
a > 10f
$$
and
$$
f_s > 10a
$$
- Then:
$$
f_s > 100f
$$
- Effect:
  - noise attenuation with minimal lag
  - filter may be ignored in modelling
  - requires very fast sampling hardware

## Practical Rule
- Choose the filter breakpoint and sample rate **together**.
- A common lecture-level rule is:
  - sample at roughly $20f$ to $30f$
  - place the anti-alias filter breakpoint below $f_s$ but around $10f$

## Links
- [[Sampling Time Selection]]
- [[Aliasing and Nyquist Criterion]]
- [[Discrete-Time Stability]]

## Visuals
![[Regulation Aliasing with Noise.png|400]]
![[Anti Alias Filter in Control Loop.png|400]]
