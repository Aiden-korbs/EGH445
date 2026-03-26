# s-Plane to z-Plane Mapping

## Mapping Equation
- Continuous-time and discrete-time domains are connected by:
$$
z = e^{sT}
$$
and
$$
s = \frac{1}{T}\ln(z)
$$

## Key Geometric Correspondence
### Left-half $s$-plane
- If:
$$
\Re(s) < 0
$$
then
$$
|z| < 1
$$
- So stable continuous poles map inside the unit circle.

### Imaginary Axis
- If:
$$
s = j\omega
$$
then
$$
z = e^{j\omega T}
$$
which lies on the **unit circle**.

### Right-half $s$-plane
- If:
$$
\Re(s) > 0
$$
then
$$
|z| > 1
$$

## Frequency Wrapping
- As $\omega$ moves from $-\infty$ to $\infty$ on the imaginary axis, the mapping traces the unit circle infinitely many times.
- This correspondence is **not unique**.
- Frequencies outside the Nyquist interval are folded back, matching the idea of **aliasing**.

## Important Insight
- In continuous time, stability is about the sign of $\Re(s)$.
- In discrete time, stability is about the magnitude $|z|$.

## Links
- [[Z Transform]]
- [[Aliasing and Nyquist Criterion]]
- [[Discrete-Time Stability]]

## Visuals
![[s Plane to z Plane Mapping.png|400]]
