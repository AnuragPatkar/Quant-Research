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