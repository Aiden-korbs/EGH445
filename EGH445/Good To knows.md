## 1. Basic Functions

These are the standard transforms used for simple polynomial or constant terms.

|**Time Domain f(t)**|**Laplace Domain F(s)**|**Notes**|
|---|---|---|
|$\delta(t)$|$1$|Unit Impulse|
|$u(t)$|$\frac{1}{s}$|Unit Step|
|$t$|$\frac{1}{s^2}$|Ramp Function|
|$t^n$|$\frac{n!}{s^{n+1}}$|For $n = 1, 2, 3 \dots$|

---

## 2. Exponential and Trigonometric

These appear most frequently when dealing with the matrix exponential $e^{At}$, especially for systems with oscillation or growth/decay.

| **Time Domain f(t)** | **Laplace Domain F(s)**         |
| -------------------- | ------------------------------- |
| $xe^{at}$            | $\frac{x}{s-a}$                 |
| $\sin(\omega t)$     | $\frac{\omega}{s^2 + \omega^2}$ |
| $\cos(\omega t)$     | $\frac{s}{s^2 + \omega^2}$      |
| $\sinh(at)$          | $\frac{a}{s^2 - a^2}$           |
| $\cosh(at)$          | $\frac{s}{s^2 - a^2}$           |

---

## 3. Shifting and Damping

If your matrix $A$ has complex eigenvalues, you will likely see these "S-domain shifting" forms during your partial fraction expansion.

|**Time Domain f(t)**|**Laplace Domain F(s)**|
|---|---|
|$e^{at}t^n$|$\frac{n!}{(s-a)^{n+1}}$|
|$e^{at}\sin(\omega t)$|$\frac{\omega}{(s-a)^2 + \omega^2}$|
|$e^{at}\cos(\omega t)$|$\frac{s-a}{(s-a)^2 + \omega^2}$|

---

## 4. Key Operational Properties

When manipulating the $(sI - A)^{-1}$ matrix algebraically, these properties help you move between domains.

- **Linearity:** $\mathcal{L}\{af(t) + bg(t)\} = aF(s) + bG(s)$
    
- **Time Scaling:** $\mathcal{L}\{f(at)\} = \frac{1}{a}F(\frac{s}{a})$
    
- **Frequency Shift:** $\mathcal{L}\{e^{at}f(t)\} = F(s-a)$
    
- **Differentiation:** $\mathcal{L}\{f'(t)\} = sF(s) - f(0)$
# Partial Fraction Decomposition Rules

**Tags:** #math #algebra #calculus

> [!warning] **Prerequisite: Proper Rational Functions Only**
> 
> Partial fraction decomposition only works for **proper rational functions**. The degree of the numerator polynomial $P(x)$ must be strictly less than the degree of the denominator polynomial $Q(x)$.
> 
> If $\text{deg}(P(x)) \geq \text{deg}(Q(x))$, you must first perform **polynomial long division** to get a polynomial plus a proper rational function.

Given a proper rational function $\frac{P(x)}{Q(x)}$, factor the denominator $Q(x)$ completely into linear and irreducible quadratic factors over the real numbers. Then, apply the following rules based on the factors present in $Q(x)$.

---

## 1. Distinct Linear Factors

For each distinct, non-repeated linear factor of the form $(ax+b)$ in the denominator, introduce a single term with a constant numerator.

**Form:**

$$\frac{P(x)}{(a_1x+b_1)(a_2x+b_2)} = \frac{A}{a_1x+b_1} + \frac{B}{a_2x+b_2}$$

**Example:**
### Step 1: Clear the Denominators

Multiply both sides of the equation by the common denominator, which is $(x-1)(x+2)$.

$$(x-1)(x+2) \left[ \frac{5x-3}{(x-1)(x+2)} \right] = (x-1)(x+2) \left[ \frac{A}{x-1} + \frac{B}{x+2} \right]$$

This cancels out the denominators, leaving you with the basic equation:

$$5x - 3 = A(x+2) + B(x-1)$$

### Step 2: Solve for the Constants

For distinct linear factors like these, the fastest way to solve for $A$ and $B$ is the **substitution method** (often called the Heaviside cover-up method). We pick strategic values for $x$ that will make one of the terms evaluate to zero.

**To find A:** Choose a value for $x$ that makes the $B$ term zero. Let $x = 1$.

$$5(1) - 3 = A(1+2) + B(1-1)$$

$$2 = 3A + 0$$

$$A = \frac{2}{3}$$

**To find B:** Choose a value for $x$ that makes the $A$ term zero. Let $x = -2$.

$$5(-2) - 3 = A(-2+2) + B(-2-1)$$

$$-10 - 3 = 0 + B(-3)$$

$$-13 = -3B$$

$$B = \frac{13}{3}$$

### Step 3: Write the Final Decomposition

Now, substitute the values of $A$ and $B$ back into your original setup.

$$\frac{5x-3}{(x-1)(x+2)} = \frac{\frac{2}{3}}{x-1} + \frac{\frac{13}{3}}{x+2}$$

This is mathematically correct, but it is standard practice to pull the denominators of the fractions down to make it look cleaner:

$$\frac{5x-3}{(x-1)(x+2)} = \frac{2}{3(x-1)} + \frac{13}{3(x+2)}$$
---

## 2. Repeated Linear Factors

For each linear factor $(ax+b)$ that is repeated $n$ times (meaning it appears as $(ax+b)^n$), introduce $n$ terms with constant numerators. The denominators will have increasing powers from $1$ up to $n$.

**Form:**

$$\frac{P(x)}{(ax+b)^n} = \frac{A_1}{ax+b} + \frac{A_2}{(ax+b)^2} + \dots + \frac{A_n}{(ax+b)^n}$$

**Example:**

$$\frac{x+5}{(x-2)^3} = \frac{A}{x-2} + \frac{B}{(x-2)^2} + \frac{C}{(x-2)^3}$$

---

## 3. Distinct Irreducible Quadratic Factors

For each non-repeated irreducible quadratic factor $(ax^2+bx+c)$ in the denominator (where the discriminant $b^2-4ac < 0$), introduce a single term with a **linear** numerator.

**Form:**

$$\frac{P(x)}{(a_1x^2+b_1x+c_1)(a_2x^2+b_2x+c_2)} = \frac{A_1x+B_1}{a_1x^2+b_1x+c_1} + \frac{A_2x+B_2}{a_2x^2+b_2x+c_2}$$

**Example:**

$$\frac{3x^2-x+4}{(x^2+1)(x^2+x+5)} = \frac{Ax+B}{x^2+1} + \frac{Cx+D}{x^2+x+5}$$

---

## 4. Repeated Irreducible Quadratic Factors

For each irreducible quadratic factor $(ax^2+bx+c)$ that is repeated $n$ times (meaning it appears as $(ax^2+bx+c)^n$), introduce $n$ terms with linear numerators. The denominators will have increasing powers from $1$ up to $n$.

**Form:**

$$\frac{P(x)}{(ax^2+bx+c)^n} = \frac{A_1x+B_1}{ax^2+bx+c} + \frac{A_2x+B_2}{(ax^2+bx+c)^2} + \dots + \frac{A_nx+B_n}{(ax^2+bx+c)^n}$$

**Example:**

$$\frac{x^3-2x}{(x^2+4)^2} = \frac{Ax+B}{x^2+4} + \frac{Cx+D}{(x^2+4)^2}$$

---

## Example: Combining Multiple Rules

If you have a complex denominator combining several of the factors above, simply chain the rules together.

**Example Setup:**

$$\frac{x^2+2x-1}{x(x-3)^2(x^2+4)} = \frac{A}{x} + \frac{B}{x-3} + \frac{C}{(x-3)^2} + \frac{Dx+E}{x^2+4}$$

- $\frac{A}{x}$: Distinct linear (Rule 1)
    
- $\frac{B}{x-3} + \frac{C}{(x-3)^2}$: Repeated linear (Rule 2)
    
- $\frac{Dx+E}{x^2+4}$: Distinct irreducible quadratic (Rule 3)
