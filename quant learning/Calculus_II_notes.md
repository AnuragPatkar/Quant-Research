# Calculus II — Lesson 1: Advanced Integration Techniques

- **Course:** Calculus II
- **Lesson:** 1
- **Priority:** CORE
- **Status:** Completed
- **Purpose:** Build the integration skills needed for probability distributions, expected values, risk modelling, and quantitative finance.

---

## 1. Why Advanced Integration Matters in Quant Finance

Integration is used to calculate:

- Probability over a continuous range.
- Expected returns and expected losses.
- Variance and higher moments.
- Option prices under continuous probability distributions.
- Tail probabilities and risk measures.
- Areas and cumulative quantities.

For a Quant Researcher, integration is not just a mathematical operation. It helps answer questions such as:

- What is the probability of a market loss exceeding $5\%$?
- What is the expected payoff of an option?
- Does a probability distribution have a finite expected value?
- Can a risk model underestimate extreme losses?

> **Hinglish Intuition:** Integration ko continuous data ka total contribution samjho. Jaise har possible market outcome ka probability-weighted contribution add karke expected return ya expected loss calculate karna.

---

## 2. Integration by Parts

### 2.1 Intuition
Integration by Parts is useful when an integrand contains the product of two functions. It is derived from the Product Rule of differentiation.

Recall:

$$
\frac{d}{dx}(uv) = u\frac{dv}{dx} + v\frac{du}{dx}
$$

Rearranging:

$$
u\,dv = d(uv) - v\,du
$$

Integrating both sides gives the Integration by Parts formula:

$$
\boxed{\int u\,dv = uv - \int v\,du}
$$

### 2.2 Formula

$$
\boxed{\int u\,dv = uv - \int v\,du}
$$

Where:
- $u$: Function selected for differentiation.
- $dv$: Remaining function multiplied by $dx$.
- $du$: Derivative of $u$, multiplied by $dx$.
- $v$: Integral of $dv$.

### 2.3 Worked Example
Evaluate:

$$
\int x e^x \, dx
$$

**Step 1:** Choose:

$$
u = x, \qquad dv = e^x \, dx
$$

**Step 2:** Differentiate and integrate:

$$
du = dx, \qquad v = e^x
$$

**Step 3:** Apply the formula:

$$
\int x e^x \, dx = x e^x - \int e^x \, dx
$$

Therefore:

$$
\boxed{\int x e^x \, dx = e^x(x - 1) + C}
$$

### 2.4 Definite Integration by Parts

$$
\boxed{\int_a^b u\,dv = [uv]_a^b - \int_a^b v\,du}
$$

Remember to apply both limits to the boundary term.

### 2.5 When to Use It
Common combinations:
- Polynomial $\times$ Exponential
- Polynomial $\times$ Logarithmic
- Polynomial $\times$ Trigonometric
- Logarithmic $\times$ Exponential

> **Hinglish:** Jab do functions multiply ho rahe hon aur direct integration difficult ho, tab ek function ko differentiate aur doosre ko integrate karte hain.

---

## 3. Partial Fractions

### 3.1 Intuition
Sometimes a rational function is difficult to integrate:

$$
\frac{P(x)}{Q(x)}
$$

Partial Fractions breaks a complicated rational expression into simpler fractions. For example:

$$
\frac{1}{x(x+2)}
$$

Can be expressed as:

$$
\frac{A}{x} + \frac{B}{x+2}
$$

The simpler fractions are easier to integrate.

### 3.2 Basic Derivation
Suppose:

$$
\frac{1}{x(x+2)} = \frac{A}{x} + \frac{B}{x+2}
$$

Multiply both sides by $x(x+2)$:

$$
1 = A(x+2) + Bx
$$

Expand and group terms:

$$
1 = Ax + 2A + Bx
$$

$$
1 = (A + B)x + 2A
$$

Compare coefficients:

$$
A + B = 0
$$

$$
2A = 1
$$

Therefore:

$$
A = \frac{1}{2}, \qquad B = -\frac{1}{2}
$$

Hence:

$$
\boxed{\frac{1}{x(x+2)} = \frac{1}{2x} - \frac{1}{2(x+2)}}
$$

### 3.3 Integration

$$
\int \frac{1}{x(x+2)} \, dx
$$

Substitute the decomposition:

$$
= \frac{1}{2} \int \frac{1}{x} \, dx - \frac{1}{2} \int \frac{1}{x+2} \, dx
$$

Therefore:

$$
\boxed{\frac{1}{2}\ln|x| - \frac{1}{2}\ln|x+2| + C}
$$

### 3.4 Important Cases

| Denominator factor | Partial fraction form |
| :--- | :--- |
| Distinct linear factors | $\frac{A}{x - a}$ |
| Repeated linear factor | $\frac{A}{x - a} + \frac{B}{(x - a)^2}$ |
| Irreducible quadratic | $\frac{Ax + B}{x^2 + bx + c}$ |
| Repeated irreducible quadratic | Include each increasing power |

### 3.5 Important Rule
Before using Partial Fractions, check the polynomial degrees. If:

$$
\deg(P) \geq \deg(Q)
$$

Perform polynomial long division first.

> **Hinglish:** Agar numerator ki degree denominator ke equal ya usse badi hai, toh pehle long division. Uske baad Partial Fractions.

---

## 4. Improper Integrals

### 4.1 Definition
An integral is called improper when:
- One or both integration limits are infinite.
- The integrand becomes unbounded or undefined at an endpoint or inside the integration interval.

Two important categories:
- **Type 1: Infinite limits**

$$
\int_a^\infty f(x) \, dx
$$

- **Type 2: Unbounded integrand** (e.g., undefined at $x = 0$)

$$
\int_0^1 \frac{1}{\sqrt{x}} \, dx
$$

### 4.2 Infinite Limits
An infinite endpoint must be replaced with a limit.

**Example:**

$$
\int_1^\infty \frac{1}{x^2} \, dx
$$

**Step 1:**

$$
= \lim_{b \to \infty} \int_1^b x^{-2} \, dx
$$

**Step 2:**

$$
= \lim_{b \to \infty} \left[ -\frac{1}{x} \right]_1^b
$$

**Step 3:**

$$
= \lim_{b \to \infty} \left( -\frac{1}{b} + 1 \right)
$$

**Final answer:**

$$
\boxed{1}
$$

The integral converges.

### 4.3 Unbounded Integrand
**Example:**

$$
\int_0^1 \frac{1}{\sqrt{x}} \, dx
$$

Since the function is undefined at zero:

$$
= \lim_{a \to 0^+} \int_a^1 x^{-1/2} \, dx
$$

Integrate:

$$
= \lim_{a \to 0^+} \left[ 2\sqrt{x} \right]_a^1
$$

$$
= \lim_{a \to 0^+} \left( 2 - 2\sqrt{a} \right)
$$

Therefore:

$$
\boxed{2}
$$

The integral converges even though the function is unbounded at the endpoint.

---

## 5. Convergence and Divergence

An improper integral can have two outcomes:
- **Convergent:** The limit exists and is finite.
- **Divergent:** The limit does not exist as a finite number.

### 5.1 The $p$-Test
Consider:

$$
\boxed{\int_1^\infty \frac{1}{x^p} \, dx}
$$

- **Convergence condition:**

$$
\boxed{p > 1}
$$

- **Divergence condition:**

$$
\boxed{p \leq 1}
$$

#### Derivation for $p \neq 1$

$$
I = \lim_{b \to \infty} \int_1^b x^{-p} \, dx
$$

Integrate:

$$
I = \lim_{b \to \infty} \left[ \frac{x^{1-p}}{1-p} \right]_1^b
$$

$$
I = \lim_{b \to \infty} \frac{b^{1-p} - 1}{1-p}
$$

- **Case 1 ($p > 1$):** Then $1 - p < 0$, so $b^{1-p} \to 0$. Therefore:

$$
I = \frac{1}{p - 1}
$$

The integral **converges**.

- **Case 2 ($p < 1$):** Then $1 - p > 0$, so $b^{1-p} \to \infty$. The integral **diverges**.

- **Case 3 ($p = 1$):** The integral becomes:

$$
\int_1^\infty \frac{1}{x} \, dx = \lim_{b \to \infty} \ln(b) = \infty
$$

It **diverges**.

#### Summary

| Condition | Result |
| :--- | :--- |
| $p > 1$ | Converges |
| $p = 1$ | Diverges |
| $p < 1$ | Diverges |

> **Important Interview Trap:** The condition is strictly $p > 1$, not $p \geq 1$.

---

## 6. Numerical Integration

Sometimes an integral cannot be evaluated easily using elementary analytical methods. Numerical Integration approximates the area under a curve.

### 6.1 Midpoint Rule
Divide the interval $[a, b]$ into $n$ equal subintervals.

**Width:**

$$
\boxed{h = \frac{b - a}{n}}
$$

**Midpoint of the $i$-th interval:**

$$
x_i^* = a + \left(i + \frac{1}{2}\right)h
$$

**Midpoint Rule:**

$$
\boxed{\int_a^b f(x) \, dx \approx h \sum_{i=0}^{n-1} f(x_i^*)}
$$

### 6.2 Visual Intuition
Imagine dividing an area under a curve into narrow rectangles:
- More rectangles generally improve approximation.
- Each rectangle uses the function value at its midpoint.
- The sum of rectangle areas approximates the total area.

> **Hinglish:** Curve ke neeche ka area chhote rectangles mein tod do. Har rectangle ka area calculate karke add kar do.

### 6.3 Python — Midpoint Rule from Scratch

```python
def midpoint_rule(f, a, b, n):
    h = (b - a) / n
    total = 0.0

    for i in range(n):
        midpoint = a + (i + 0.5) * h
        total += f(midpoint)

    return h * total


def f(x):
    return x**2


result = midpoint_rule(f, 0, 2, 100)

print(result)
```

- **Expected output:** approximately `2.6666...`
- **Exact value:**

$$
\int_0^2 x^2 \, dx = \frac{8}{3}
$$

### 6.4 Complexity
For $n$ subintervals:
- **Time complexity:** $O(n)$
- **Extra space complexity:** $O(1)$

### 6.5 Pitfalls
- Increasing the upper limit without increasing $n$ can increase interval width.
- A fixed number of rectangles does not guarantee accuracy.
- Numerical approximation is not automatically equal to the analytical answer.
- Check convergence by increasing numerical resolution.

---

## 7. SciPy Numerical Integration

SciPy provides numerical integration through `scipy.integrate.quad`.

### Example: Infinite Endpoint
Evaluate:

$$
I = \int_1^\infty \frac{1}{x^2} \, dx
$$

```python
from scipy.integrate import quad

def f(x):
    return 1 / x**2

result, error = quad(f, 1, float("inf"))

print("Integral:", result)
print("Estimated error:", error)
```

- **Expected result:** `Integral: approximately 1.0`
- The second returned value is an estimate of numerical integration error.

> **Important:** Numerical error estimates are not guarantees that the model, input data, or mathematical assumptions are correct.

---

## 8. Quant Finance Application — Expected Value

Expected value is the probability-weighted average of possible outcomes.

For a continuous random variable:

$$
\boxed{E[X] = \int_{-\infty}^{\infty} x f(x) \, dx}
$$

Where:
- $X$: Random variable.
- $f(x)$: Probability density function.
- $x f(x)$: Probability-weighted contribution.

For a finite expected absolute value, we require:

$$
\boxed{\int_{-\infty}^{\infty} |x| f(x) \, dx < \infty}
$$

This condition ensures the expectation is well-defined and finite.

### 8.1 Valid Distribution Does Not Guarantee Finite Mean
A probability density must satisfy:

$$
\int_{-\infty}^{\infty} f(x) \, dx = 1
$$

But this does **not** guarantee:

$$
E[|X|] < \infty
$$

A valid probability distribution can have an infinite expected value.

---

## 9. Pareto Distribution and Heavy Tails

A Pareto distribution is a useful example of a heavy-tailed distribution. Its probability density function is:

$$
\boxed{f(x) = \frac{\alpha}{x^{\alpha+1}}, \quad x \geq 1, \ \alpha > 0}
$$

### 9.1 Expected Value

$$
E[X] = \int_1^\infty x f(x) \, dx
$$

Substitute $f(x)$:

$$
E[X] = \alpha \int_1^\infty x^{-\alpha} \, dx
$$

Using the $p$-test:

$$
\boxed{E[X] = \frac{\alpha}{\alpha - 1}, \quad \alpha > 1}
$$

For $0 < \alpha \leq 1$, the expected value diverges.

### 9.2 Variance
For this Pareto distribution:

$$
E[X^2] = \frac{\alpha}{\alpha - 2}, \quad \alpha > 2
$$

Consequently:

| Shape parameter | Mean | Variance |
| :--- | :--- | :--- |
| $0 < \alpha \leq 1$ | Infinite | Infinite |
| $1 < \alpha \leq 2$ | Finite | Infinite |
| $\alpha > 2$ | Finite | Finite |

### 9.3 Important Risk Interpretation
A distribution can have:
- A finite expected loss.
- An infinite variance.
- Extremely heavy tails.

A finite average does not imply that extreme losses are manageable.

> **Hinglish:** Average loss manageable dikh sakta hai, lekin extreme losses bahut bade ho sakte hain. Isliye Quant Risk Manager ko sirf mean nahi, tail behaviour aur variance bhi check karna chahiye.

---

## 10. Quant Research Applications

| Technique | Quant Finance Application |
| :--- | :--- |
| Integration by Parts | Expected payoff derivations and analytical probability calculations |
| Partial Fractions | Simplifying rational integrals |
| Improper Integrals | Infinite-tail probability and expectation calculations |
| $p$-Test | Checking convergence of heavy-tailed moments |
| Midpoint Rule | Numerical approximation of finite integrals |
| SciPy `quad` | Numerical integration over finite and infinite intervals |
| Expected Value | Average return, payoff, or loss |
| Pareto Distribution | Modelling heavy-tailed outcomes |

### Theory vs. Reality
Mathematical convergence does not automatically imply a reliable empirical risk estimate. Real financial data may have:
- Regime changes.
- Limited observations in the extreme tail.
- Dependence and volatility clustering.
- Transaction costs and liquidity constraints.
- Estimation uncertainty.

A mathematically finite expected loss is not a guarantee of low financial risk.

---

## 11. Common Mistakes and Interview Traps

1. **Using the wrong $p$-test condition**
   - Incorrect: $p \geq 1$
   - Correct: $p > 1$
2. **Treating infinity as an ordinary endpoint**
   - Always express improper integrals as limits.
3. **Ignoring an undefined endpoint**
   - Replace it with a one-sided limit.
4. **Forgetting the integration constant**
   - Indefinite integrals require $+ C$.
5. **Incorrect endpoint substitution**
   - For definite integrals, calculate upper endpoint minus lower endpoint.
6. **Confusing convergence of probability with convergence of expectation**
   - Total probability equal to $1$ does not guarantee a finite mean.
7. **Assuming finite mean means finite variance**
   - These are different mathematical conditions.
8. **Confusing numerical approximation with exact integration**
   - Always distinguish approximation error from the exact result.

---

## 12. Cheat Sheet — Formulas to Memorize

- **Integration by Parts**

$$
\boxed{\int u\,dv = uv - \int v\,du}
$$

- **Partial Fractions**

$$
\frac{1}{x(x+a)} = \frac{1}{a}\cdot\frac{1}{x} - \frac{1}{a}\cdot\frac{1}{x+a}
$$

- **Improper Integral**

$$
\boxed{\int_a^\infty f(x) \, dx = \lim_{b \to \infty} \int_a^b f(x) \, dx}
$$

- **$p$-Test**

$$
\boxed{\int_1^\infty \frac{1}{x^p} \, dx \quad \begin{cases} \text{Converges}, & p > 1 \\ \text{Diverges}, & p \leq 1 \end{cases}}
$$

- **Midpoint Rule**

$$
\boxed{I \approx h \sum_{i=0}^{n-1} f\left(a + \left(i + \frac{1}{2}\right)h\right)}
$$

- **Expected Value**

$$
\boxed{E[X] = \int_{-\infty}^{\infty} x f(x) \, dx}
$$

- **Pareto Mean**

$$
\boxed{E[X] = \frac{\alpha}{\alpha - 1}, \quad \alpha > 1}
$$

---

## 13. Three-Line Hinglish Revision

1. **Integration by Parts** aur **Partial Fractions** complicated integrals ko simpler banate hain.
2. **Improper Integral** mein infinity ya undefined endpoint ko limit se handle karte hain; **$p$-test** mein $p > 1$ par convergence hoti hai.
3. Valid probability distribution ka mean ya variance zaroori nahi finite ho — **heavy tails** ko risk modelling mein carefully examine karna padta hai.

> **Final Quant Researcher Takeaway:** Integration helps calculate expected outcomes, but convergence analysis tells us whether those expectations actually exist. In quantitative finance, knowing when a mathematical quantity is infinite can be just as important as knowing how to calculate it.
calculus_ii_lesson_1_advanced_integration-v2.md
Displaying calculus_ii_lesson_1_advanced_integration-v2.md.


# Calculus II — Lesson 2: Trigonometric Integrals

**Priority:** CORE  
**Status:** Completed  
**Estimated study time:** 60–90 minutes  
**Prerequisites:** Basic integration, Power Rule, trigonometric identities, U-substitution.

---

## 1. Why Trigonometric Integrals Matter

Trigonometric integrals involve functions such as:

$$
\int \sin^m x \cos^n x \, dx
$$

and

$$
\int \tan^m x \sec^n x \, dx
$$

They are useful for:

- Probability and distribution calculations.
- Mathematical modelling.
- Fourier analysis and signal processing.
- Analytical derivations in quantitative finance.
- Understanding transformations involving periodic functions.

**Hinglish intuition:** Trigonometric integrals mein main challenge integration karna nahi, balki correct identity aur substitution choose karna hai.

---

## 2. Fundamental Trigonometric Identities

### Pythagorean identities

$$
\boxed{\sin^2 x + \cos^2 x = 1}
$$

Rearranging:

$$
\sin^2 x = 1 - \cos^2 x
$$

$$
\cos^2 x = 1 - \sin^2 x
$$

For tangent and secant:

$$
\boxed{1 + \tan^2 x = \sec^2 x}
$$

$$
\boxed{\sec^2 x - \tan^2 x = 1}
$$

### Power-reduction identities

These are derived from double-angle identities.

$$
\boxed{\sin^2 x = \frac{1 - \cos 2x}{2}}
$$

$$
\boxed{\cos^2 x = \frac{1 + \cos 2x}{2}}
$$

These are especially useful when both sine and cosine have even powers.

### Derivative identities

$$
\frac{d}{dx}\sin x = \cos x
$$

$$
\frac{d}{dx}\cos x = -\sin x
$$

$$
\frac{d}{dx}\tan x = \sec^2 x
$$

$$
\frac{d}{dx}\sec x = \sec x \tan x
$$

**Important:** Integration strategies are derived from identities and derivative matching, not arbitrary memorization.

---

## 3. Strategy 1: Odd Power of Sine

Consider:

$$
I = \int \sin^m x \cos^n x \, dx
$$

When the sine power is odd:

1. Save one sine factor.
2. Convert remaining sine powers using $\sin^2 x = 1 - \cos^2 x$.
3. Substitute $u = \cos x$.

### Worked example

$$
I = \int \sin^3 x \cos^2 x \, dx
$$

Step 1: Save one sine.

$$
I = \int \sin^2 x \cos^2 x \sin x \, dx
$$

Step 2: Apply identity.

$$
I = \int (1 - \cos^2 x)\cos^2 x \sin x \, dx
$$

Step 3: Substitute.

$$
u = \cos x, \qquad du = -\sin x \, dx
$$

Therefore:

$$
I = -\int (1 - u^2)u^2 \, du
$$

$$
I = -\int (u^2 - u^4) \, du
$$

Integrating:

$$
I = -\frac{u^3}{3} + \frac{u^5}{5} + C
$$

Substitute back:

$$
\boxed{I = -\frac{\cos^3 x}{3} + \frac{\cos^5 x}{5} + C}
$$

---

## 4. Strategy 2: Odd Power of Cosine

When cosine has an odd power:

1. Save one cosine factor.
2. Convert remaining cosine powers using $\cos^2 x = 1 - \sin^2 x$.
3. Substitute $u = \sin x$.

### Worked example

$$
I = \int \sin^4 x \cos^3 x \, dx
$$

Save one cosine:

$$
I = \int \sin^4 x \cos^2 x \cos x \, dx
$$

Apply identity:

$$
I = \int \sin^4 x (1 - \sin^2 x) \cos x \, dx
$$

Substitute:

$$
u = \sin x, \qquad du = \cos x \, dx
$$

Therefore:

$$
I = \int u^4(1 - u^2) \, du
$$

$$
I = \int (u^4 - u^6) \, du
$$

$$
I = \frac{u^5}{5} - \frac{u^7}{7} + C
$$

Final answer:

$$
\boxed{I = \frac{\sin^5 x}{5} - \frac{\sin^7 x}{7} + C}
$$

---

## 5. Strategy 3: Both Powers Even

When both sine and cosine have even powers, use power-reduction identities.

### Worked example

$$
I = \int \sin^2 x \cos^2 x \, dx
$$

Apply identities:

$$
I = \int \left(\frac{1 - \cos 2x}{2}\right)\left(\frac{1 + \cos 2x}{2}\right) dx
$$

Multiply:

$$
I = \frac{1}{4} \int (1 - \cos^2 2x) \, dx
$$

Using:

$$
1 - \cos^2 2x = \sin^2 2x
$$

Therefore:

$$
I = \frac{1}{4} \int \sin^2 2x \, dx
$$

Apply power reduction:

$$
\sin^2 2x = \frac{1 - \cos 4x}{2}
$$

Thus:

$$
I = \frac{1}{8} \int (1 - \cos 4x) \, dx
$$

Integrate:

$$
I = \frac{x}{8} - \frac{\sin 4x}{32} + C
$$

Final answer:

$$
\boxed{I = \frac{x}{8} - \frac{\sin 4x}{32} + C}
$$

**Important:** When integrating $\cos 4x$, remember the chain-rule factor:

$$
\int \cos 4x \, dx = \frac{\sin 4x}{4} + C
$$

---

## 6. Strategy 4: Tangent and Secant Integrals

Consider:

$$
\int \tan^m x \sec^n x \, dx
$$

Two important derivative matches:

$$
\frac{d}{dx}\tan x = \sec^2 x
$$

$$
\frac{d}{dx}\sec x = \sec x \tan x
$$

### Case A: Even power of secant

Save $\sec^2 x$, substitute:

$$
u = \tan x
$$

Use:

$$
\sec^2 x = 1 + \tan^2 x
$$

Example:

$$
I = \int \tan^3 x \sec^2 x \, dx
$$

Let:

$$
u = \tan x, \qquad du = \sec^2 x \, dx
$$

Then:

$$
I = \int u^3 \, du
$$

$$
\boxed{I = \frac{\tan^4 x}{4} + C}
$$

### Case B: Odd power of tangent

Save $\sec x \tan x$, substitute:

$$
u = \sec x
$$

Use:

$$
\tan^2 x = \sec^2 x - 1
$$

Example:

$$
I = \int \tan^3 x \sec^3 x \, dx
$$

Rewrite:

$$
I = \int \tan^2 x \sec^2 x (\sec x \tan x) \, dx
$$

Substitute:

$$
u = \sec x, \qquad du = \sec x \tan x \, dx
$$

Then:

$$
I = \int (u^2 - 1)u^2 \, du
$$

$$
I = \int (u^4 - u^2) \, du
$$

Final answer:

$$
\boxed{I = \frac{\sec^5 x}{5} - \frac{\sec^3 x}{3} + C}
$$

---

## 7. Quick Strategy Selection Table

| Integrand pattern | Recommended strategy |
| :--- | :--- |
| Odd sine power | Save one sine; $u = \cos x$ |
| Odd cosine power | Save one cosine; $u = \sin x$ |
| Both powers even | Power reduction |
| Even secant power | Save $\sec^2 x$; $u = \tan x$ |
| Odd tangent power | Save $\sec x \tan x$; $u = \sec x$ |

**Remember:** These are useful strategies, not universal laws. Always check whether your substitution simplifies the integral.

---

## 8. Numerical Integration Using Python

Analytical integration is not always convenient or possible.

For numerical definite integration, SciPy provides:

```python
from scipy.integrate import quad

result, error = quad(function, lower_limit, upper_limit)
```

- `result`: Numerical integral estimate.
- `error`: Estimated absolute numerical integration error.

### Example 1: Integrate a trigonometric function

Calculate:

$$
I = \int_0^{\pi/2} \sin^3 x \cos^2 x \, dx
$$

Analytical answer:

$$
I = \frac{2}{15} \approx 0.1333333
$$

Python implementation:

```python
import numpy as np
from scipy.integrate import quad

# Define the integrand
def f(x):
    return np.sin(x)**3 * np.cos(x)**2

# Numerical integration
result, error = quad(f, 0, np.pi/2)

# Analytical result
analytical = 2/15

# Absolute difference
difference = abs(result - analytical)

print("Numerical result:", result)
print("Estimated error:", error)
print("Analytical result:", analytical)
print("Absolute difference:", difference)
```

### Example 2: Both powers even

Calculate:

$$
I = \int_0^{\pi/2} \sin^2 x \cos^2 x \, dx
$$

Analytical answer:

$$
I = \frac{\pi}{16}
$$

Python:

```python
import numpy as np
from scipy.integrate import quad

def g(x):
    return np.sin(x)**2 * np.cos(x)**2

result, error = quad(g, 0, np.pi/2)

analytical = np.pi / 16

difference = abs(result - analytical)

print("Numerical result:", result)
print("Estimated error:", error)
print("Analytical result:", analytical)
print("Absolute difference:", difference)
```

Observed output:

```text
Numerical result: 0.19634954084936207
Estimated error: 2.179917811255395e-15
Analytical result: 0.19634954084936207
Absolute difference: 0.0
```

The two computed floating-point results match. This does not mean mathematical error is necessarily zero.

---

## 9. Understanding Numerical Tolerances

SciPy's `quad()` accepts:

- `epsabs`: Requested absolute error tolerance.
- `epsrel`: Requested relative error tolerance.

Example:

```python
result, error = quad(
    f,
    0,
    np.pi/2,
    epsabs=1e-10,
    epsrel=1e-10
)
```

A simplified description of the error acceptance criterion is:

$$
\boxed{\text{Error estimate} \lesssim \max(\text{epsabs}, \text{epsrel}|I|)}
$$

These are requested tolerances, not guaranteed bounds on the true error.

### Numerical example

Suppose:

$$
I = 20
$$

$$
\text{epsabs} = 0.005
$$

$$
\text{epsrel} = 0.001
$$

Relative component:

$$
0.001 \times 20 = 0.02
$$

Simplified threshold:

$$
\max(0.005, 0.02) = 0.02
$$

---

## 10. Numerical Validation: Researcher's Mindset

A small error estimate does not guarantee that a calculation is correct.

When no analytical solution is available, confidence can be improved through:

- Independent numerical methods.
- Convergence testing with tighter tolerances.
- Splitting the integration interval and comparing results.
- Mathematical sanity checks.
- Sensitivity testing and inspection of tail contributions.

### Other important checks

- Verify the integrand and integration limits.
- Confirm radians versus degrees.
- Check probability bounds when integrating probability densities.
- Check dimensions and expected magnitudes.

### Research principle

$$
\boxed{\text{Numerical accuracy} \neq \text{Implementation correctness}}
$$

One successful test case does not establish universal correctness.

---

## 11. Quant Finance Applications

### A. Probability calculations

Probability densities often require integration:

$$
P(a < X < b) = \int_a^b f_X(x) \, dx
$$

### B. Option pricing

Risk-neutral pricing can involve expectations:

$$
V_0 = e^{-rT} \mathbb{E}^{\mathbb{Q}}[H(S_T)]
$$

For continuous distributions, expectations can become integrals.

### C. Risk measurement

Tail probabilities and expected shortfall calculations may require numerical integration, especially for complicated distributions.

### Theory vs Reality

Real financial models may contain:

- Heavy tails.
- Discontinuous payoffs.
- Singularities.
- Complicated distributions.
- Numerical instability.

A mathematically valid numerical answer still requires model validation and economic interpretation.

---

## 12. Common Mistakes

- Forgetting the chain-rule factor when integrating expressions such as $\cos 4x$.
- Choosing substitution without checking derivative matching.
- Using degrees instead of radians in NumPy.
- Assuming a small `quad()` error estimate proves correctness.
- Confusing estimated numerical error with standard deviation.
- Treating agreement on one test case as universal validation.
- Forgetting the constant of integration ($+C$) in indefinite integration.

---

## 13. Interview Takeaways

Be ready to explain:

- Why odd sine powers suggest $u = \cos x$.
- Why odd cosine powers suggest $u = \sin x$.
- Why power-reduction identities work for even powers.
- Why numerical and analytical solutions should be compared when possible.
- What SciPy's `quad()` error output represents.
- Why a small estimated error does not guarantee correctness.
- How to validate numerical integration without an analytical solution.

---

## 14. Cheat Sheet

### Formulas to memorize

$$
\sin^2 x + \cos^2 x = 1
$$

$$
\sin^2 x = \frac{1 - \cos 2x}{2}
$$

$$
\cos^2 x = \frac{1 + \cos 2x}{2}
$$

$$
1 + \tan^2 x = \sec^2 x
$$

$$
\frac{d}{dx}\tan x = \sec^2 x
$$

$$
\frac{d}{dx}\sec x = \sec x \tan x
$$

### Three-line Hinglish revision

1. Odd power ho toh ek factor save karke derivative matching substitution choose karo.
2. Dono powers even hon toh power-reduction identities lagao.
3. Numerical answer ko blindly trust mat karo; independent validation aur convergence checks karo.
calculus_ii_lesson_2_trigonometric_integrals.md
Displaying calculus_ii_lesson_2_trigonometric_integrals.md.