# Quant Finance Calculus I — Lessons 1–4 Study Notes

## Current Progress
* **Mode:** Full Syllabus
* **Goal:** Job-ready Quant Researcher
* **Completed:** Limits, Derivative Intuition, Difference Quotient, First Principles, Power Rule, Product Rule, Logarithmic & Exponential Functions
* **Next:** Calculus I — Lesson 5: Related Rates & Linear Approximation

---

## Lesson 1 — Limits & Continuity

### Core Definitions

#### Limit
A limit describes the value that a function approaches as the input approaches a particular value.

$$\lim_{x\to a} f(x) = L$$

means that as $x$ gets arbitrarily close to $a$, $f(x)$ gets arbitrarily close to $L$.

#### Continuity
A function is continuous at $x = a$ when:
1. $f(a)$ exists.
2. $\lim_{x\to a} f(x)$ exists.
3. $\lim_{x\to a} f(x) = f(a)$.

### Hinglish Intuition
* **Limit** ka matlab hai: *"x kisi value ke paas ja raha hai, toh function kis value ke paas ja raha hai?"*
* **Continuity** ka matlab roughly: graph mein us point par break/jump/hole nahi hai.

---

## Lesson 2 — The Derivative

### Average Rate of Change
For two points $(x_1, x_2)$:

$$\frac{f(x_2) - f(x_1)}{x_2 - x_1}$$

It measures the change between two points.

### Instantaneous Rate of Change
The derivative measures the rate of change at one point:

$$f'(x) = \lim_{h\to 0} \frac{f(x+h) - f(x)}{h}$$

### Important Distinction
* **Average rate** $\rightarrow$ two points, no limit required.
* **Instantaneous rate** $\rightarrow$ one point, obtained by taking a limit.

### Hinglish Intuition
* **Average rate** = do checkpoints ke beech average speed.
* **Instantaneous rate** = exactly us moment par speedometer kya dikha raha hai.

---

## Lesson 3 — Power Rule & Product Rule

### Power Rule
For:

$$f(x) = x^n$$

the derivative is:

$$\boxed{\frac{d}{dx} x^n = n x^{n-1}}$$

**Example:**

$$\frac{d}{dx} x^5 = 5x^4$$

### Product Rule
For:

$$f(x) = u(x)v(x)$$

$$\boxed{(uv)' = u'v + uv'}$$

### Hinglish Intuition
Do functions multiply ho rahe hain, toh simply dono ko separately differentiate karke multiply nahi kar sakte.

**Product Rule:**
> first derivative $\times$ second $+$ first $\times$ second derivative

---

## Lesson 4 — Logarithmic & Exponential Functions

### Exponential Function
$$f(x) = a^x, \qquad a > 0, \ a \neq 1$$

The variable appears in the exponent.

**Example:** $2^x$

### Logarithmic Function
$$f(x) = \log_a x$$

A logarithm asks: *"What exponent do I need?"*

$$2^3 = 8 \implies \log_2(8) = 3$$

Exponential and logarithmic functions are **inverse functions**.

### Natural Exponential Function
The special base is:

$$e \approx 2.71828$$

The key derivative is:

$$\boxed{\frac{d}{dx} e^x = e^x}$$

This is why $e^x$ is extremely important in quantitative finance.

### General Exponential Derivative
$$\boxed{\frac{d}{dx} a^x = a^x \ln(a)}$$

**Example:**

$$\frac{d}{dx} 3^x = 3^x \ln 3$$

### Natural Logarithm
$$\ln(x) = \log_e(x)$$

**Important values:**
* $\ln 1 = 0$
* $\ln e = 1$
* $\ln(e^3) = 3$

For real-valued logarithms:

$$\boxed{x > 0}$$

### Logarithm Identities
* **Product:**
  $$\boxed{\ln(ab) = \ln a + \ln b}$$
* **Quotient:**
  $$\boxed{\ln\left(\frac{a}{b}\right) = \ln a - \ln b}$$
* **Power:**
  $$\boxed{\ln(a^n) = n\ln a}$$
* **Inverse identities:**
  $$\boxed{\ln(e^x) = x}$$
  and, for $x > 0$:
  $$\boxed{e^{\ln x} = x}$$

### Logarithm Derivative
$$\boxed{\frac{d}{dx} \ln x = \frac{1}{x}}$$

More generally:

$$\boxed{\frac{d}{dx} \log_a x = \frac{1}{x \ln a}}$$

> **Important Correction from Checkpoint:**
> Do not derive $\frac{d}{dx}\ln x$ using $\log(e) \cdot e^x$. That expression is related to differentiating an exponential, not $\ln x$.
>
> The correct result is:
> $$\boxed{\frac{d}{dx} \ln x = \frac{1}{x}}$$
> The two derivatives are different because $e^x$ and $\ln x$ are inverse functions.

---

## Lesson 4 — Worked Examples

1. **Example 1:**
   $$f(x) = e^x + 5x^3 \implies f'(x) = e^x + 15x^2$$
2. **Example 2:**
   $$f(x) = 3^x \implies f'(x) = 3^x \ln 3$$
3. **Example 3:**
   $$f(x) = 4\ln x + 3x^2 \implies f'(x) = \frac{4}{x} + 6x$$
4. **Example 4:**
   Using the product/power log identities (for $x > 0$):
   $$\ln(5x^2) = \ln 5 + 2\ln x$$

---

## Quant Finance Application — Returns & Compounding

### Simple Return
$$\boxed{R = \frac{P_1 - P_0}{P_0} = \frac{P_1}{P_0} - 1}$$

### Log Return
$$\boxed{r = \ln\left(\frac{P_1}{P_0}\right)}$$

**Example:** Price moves from ₹20,000 to ₹21,000.
* **Simple return:**
  $$R = \frac{21000 - 20000}{20000} = 0.05 = 5\%$$
* **Log return:**
  $$r = \ln(1.05) \approx 0.04879 = 4.879\%$$

They differ because the log return applies a logarithmic transformation to the gross return.

### Why Log Returns Are Useful
Suppose $P_0 \rightarrow P_1 \rightarrow P_2$. Then:

$$\ln\left(\frac{P_1}{P_0}\right) + \ln\left(\frac{P_2}{P_1}\right) = \ln\left(\frac{P_2}{P_0}\right)$$

So **log returns are additive across time**. This is one major reason they are widely used in quantitative finance.

### Continuous Compounding
Continuous compounding gives:

$$\boxed{FV = PV \cdot e^{rT}}$$

The corresponding discount factor is:

$$\boxed{DF = e^{-rT}}$$

This connects exponential functions directly to pricing and discounting.

---

## Python Exercises

### From Scratch — Simple & Log Returns

```python
import math

def simple_return(p0, p1):
    return (p1 / p0) - 1

def log_return(p0, p1):
    return math.log(p1 / p0)

print(simple_return(20000, 21000))
print(log_return(20000, 21000))
```

**Expected approximate output:**
```text
0.05
0.048790164...
```

### NumPy Vectorization

```python
import numpy as np

prices = np.array([100, 102, 101, 105, 108])

log_returns = np.log(prices[1:] / prices[:-1])

print(log_returns)
print(log_returns.shape)
```

For $n$ prices, the number of adjacent log returns is:

$$n - 1$$

### Coding Pitfalls
* Do not use zero or negative prices inside `log`.
* Be careful with floating-point precision.
* Do not confuse simple returns with log returns.
* Random arrays are fine for coding practice, but real market data have economic structure.
* In quantitative research, avoid look-ahead bias and data leakage.

---

## Lesson 4 Checkpoint — Questions & Answers

### Q1. Difference between exponential and logarithmic functions
They are inverse functions. In an exponential function, the variable appears as the exponent ($2^x$). A logarithm asks which exponent is required: $\log_2(8) = 3$ because $2^3 = 8$.

### Q2. Why is $e^x$ special?
Because $\frac{d}{dx} e^x = e^x$. The function is unchanged by differentiation.

### Q3. Why must a real logarithm have a positive input?
Because $e^y > 0$ for every real $y$. Therefore no real exponent can produce zero or a negative number.

### Q4. Why are log returns additive?
Because $\ln(ab) = \ln a + \ln b$. Therefore consecutive log returns can be summed.

### Q5. Why does exponential growth accelerate?
Because a constant percentage growth rate produces increasingly larger absolute changes.
**Example:** $100 \rightarrow 110 \rightarrow 121 \rightarrow 133.1$ (increments are $10, 11, 12.1$).

---

## Lesson 4 Numerical Practice — Completed

1. $f(x) = 7e^x + 4x^3 \implies \boxed{f'(x) = 7e^x + 12x^2}$
2. $f(x) = 5\ln x + 3x^2 \implies \boxed{f'(x) = \frac{5}{x} + 6x}$
3. Price moves from ₹500 to ₹550:
   * **Simple return:** $10\%$
   * **Log return:** $\ln(1.10) \approx 9.531\%$
   * **Difference:** $10 - 9.531 = 0.469$ percentage points.

---

## Lesson 4 Interview Questions
1. Why is $\frac{d}{dx}e^x = e^x$?
2. Derive $\frac{d}{dx}\ln x$.
3. Why are log returns useful in quantitative finance?
4. Explain continuous compounding.
5. A stock falls 50% and then rises 50%. Compare simple and log returns.
6. Explain simple returns vs log returns to a portfolio manager without using calculus.

---

## Lesson 4 Cheat Sheet

### Definitions
* **Limit** $\rightarrow$ value a function approaches.
* **Derivative** $\rightarrow$ instantaneous rate of change.
* **Exponential** $\rightarrow$ variable appears in exponent.
* **Logarithm** $\rightarrow$ asks for the required exponent.
* **$e^x$** $\rightarrow$ natural exponential function.
* **$\ln x$** $\rightarrow$ natural logarithm.

### Formulas
* $\frac{d}{dx}x^n = nx^{n-1}$
* $\frac{d}{dx}e^x = e^x$
* $\frac{d}{dx}a^x = a^x\ln a$
* $\frac{d}{dx}\ln x = \frac{1}{x}$
* $\frac{d}{dx}\log_a x = \frac{1}{x\ln a}$
* $\ln(ab) = \ln a + \ln b$
* $\ln(a/b) = \ln a - \ln b$
* $\ln(a^n) = n\ln a$
* $R = \frac{P_1 - P_0}{P_0}$
* $r = \ln(P_1 / P_0)$
* $FV = PV e^{rT}$

### 3-Line Hinglish Revision
1. Exponential mein variable exponent mein hota hai.
2. Logarithm poochta hai kaunsa exponent chahiye.
3. Quant mein log returns useful hain kyunki time ke across add ho sakte hain.

---

## Error Log
* **Difference quotient sign** $\rightarrow$ use $f(x+h) - f(x)$.
* **$(+C)$ in derivative** $\rightarrow$ $(+C)$ belongs to indefinite integration.
* **$(h=0)$ wording** $\rightarrow$ derivative definition uses $h \to 0$, not direct $h = 0$.
* **Constant derivative** $\rightarrow$ zero.
* **Coefficient collection** $\rightarrow$ combine every term carefully.
* **Log-return difference** $\rightarrow$ $10\% - 9.531\% = 0.469$ percentage points.
* **Central difference formula** $\rightarrow$ not yet learned; defer numerical differentiation.
quant_finance_calculus_notes_lessons_1_4.md
Displaying quant_finance_calculus_notes_lessons_1_4.md.



# Calculus I — Lessons 5–8

## Complete Revision Notes + Quant Research Cheat Sheet

**Track:** Quant Finance Mathematics · Full Syllabus  
**Coverage:** Lesson 5 to Lesson 8  
**Prepared:** 24 November 2026  
**Language:** Professional English + Roman Hinglish  
**Purpose:** Concept revision, interview preparation, and practical quant-research reference

> **How to use these notes:** First understand the intuition, then reproduce the derivations without looking, solve the worked examples, and finally use the cheat sheet for spaced revision. These notes do not replace independent practice.

---

## Contents

- [Lesson 5 — Related Rates and Linear Approximation](#lesson-5--related-rates-and-linear-approximation)
- [Lesson 6 — Mean Value Theorem and Curve Sketching](#lesson-6--mean-value-theorem-and-curve-sketching)
- [Lesson 7 — Applications of Calculus](#lesson-7--applications-of-calculus)
- [Lesson 8 — The Integral](#lesson-8--the-integral)
- [Master Cheat Sheet — Lessons 5 to 8](#master-cheat-sheet--lessons-5-to-8)
- [Common Mistakes and Corrections](#common-mistakes-and-corrections)
- [Quant Research Connections](#quant-research-connections)
- [Active Recall Questions (No Solutions)](#active-recall-questions-no-solutions)

---

## Lesson 5 — Related Rates and Linear Approximation

**Priority:** CORE  
**Core idea:** Use derivatives to connect changing quantities and to estimate nearby function values.  
**Why it matters for a Quant Researcher:** Sensitivity analysis, option Greeks, risk approximations, and model dynamics all rely on understanding how one quantity responds to another.

### 5.1 Intuition

#### Related rates
Two quantities may change together. If a circle's radius increases, its area increases too. Related-rates problems ask how quickly one quantity changes when another quantity is changing.

**Hinglish:** Radius badhega toh area bhi badhega. Related rates batata hai ki radius jis speed se badh raha hai, uske kaaran area kitni speed se badh raha hai.

#### Linear approximation
A smooth curve looks almost like its tangent line when we zoom in sufficiently close to a point.

**Hinglish:** Kisi point ke bilkul paas curve ko tangent line se approximate kar sakte hain. Isse nearby value ka quick estimate milta hai.

### 5.2 Related-rates formula

If $y$ depends on $x$, and $x$ depends on time $t$, the chain rule gives:

$$\boxed{\frac{dy}{dt} = \frac{dy}{dx}\frac{dx}{dt}}$$

Interpretation:
- $\frac{dy}{dt}$: rate at which $y$ changes with time.
- $\frac{dy}{dx}$: sensitivity of $y$ to $x$.
- $\frac{dx}{dt}$: rate at which $x$ changes with time.

This formula requires the relevant functions to be differentiable and the chain rule to apply.

#### Reliable method for related-rates questions
1. Draw or describe the relationship between the variables.
2. Write an equation connecting the variables.
3. Differentiate both sides with respect to time $t$.
4. Substitute the known instantaneous values and rates.
5. Solve, including units and direction (increasing/decreasing).

**Important:** Differentiate before substituting instantaneous values. A changing variable is not a constant.

### 5.3 Worked example — expanding circle

The area of a circle is:

$$A = \pi r^2$$

Differentiate with respect to time:

$$\frac{dA}{dt} = 2\pi r \frac{dr}{dt}$$

Suppose $r = 5$ units and $\frac{dr}{dt} = 2$ units/second:

$$\frac{dA}{dt} = 2\pi(5)(2) = 20\pi$$

$$\boxed{\frac{dA}{dt} = 20\pi \text{ square units/second}}$$

The area is increasing at this instantaneous rate.

### 5.4 Linear approximation / linearization

Near $x = a$, approximate $f(x)$ with the tangent line at $a$:

$$\boxed{L(x) = f(a) + f'(a)(x - a)}$$

Where:
- $f(a)$ is the known value at the base point.
- $f'(a)$ is the slope at the base point.
- $x - a$ is the small movement from the base point.

The approximation is generally better when $x$ is close to $a$, assuming sufficient smoothness.

#### Worked example — estimate $\sqrt{101}$

Let $f(x) = \sqrt{x}$ and choose $a = 100$.

$$f(100) = 10$$

$$f'(x) = \frac{1}{2\sqrt{x}} \quad \Rightarrow \quad f'(100) = \frac{1}{20}$$

Linear approximation:

$$L(101) = 10 + \frac{1}{20}(101 - 100)$$

$$\boxed{\sqrt{101} \approx 10.05}$$

Actual value is approximately $10.0498756$. The approximation is close because $101$ is near $100$.

### 5.5 Quant-finance connections

#### First-order sensitivity
For a small change $\Delta x$:

$$\Delta f \approx f'(x)\,\Delta x$$

For an option price $V(S)$, a small underlying-price movement can be approximated by:

$$\Delta V \approx \Delta_{\text{option}}\,\Delta S$$

Here option Delta is the first derivative of option value with respect to underlying price.

For larger moves, first-order approximation may be insufficient. A second-order approximation includes Gamma:

$$\Delta V \approx \Delta\,\Delta S + \frac{1}{2}\Gamma(\Delta S)^2$$

This is a local approximation, not an exact realized P&L formula. Volatility, time, rates, dividends, liquidity, and market frictions can also change.

### 5.6 Python — linear approximation

```python
import math

def linear_approx_sqrt(x, a=100):
    # Function value at the expansion point
    f_a = math.sqrt(a)

    # Derivative of sqrt(x), evaluated at a
    derivative_a = 1 / (2 * math.sqrt(a))

    # Tangent-line approximation
    return f_a + derivative_a * (x - a)

x = 101
estimate = linear_approx_sqrt(x)
actual = math.sqrt(x)

print("Estimate:", estimate)
print("Actual:", actual)
print("Absolute error:", abs(actual - estimate))
```

**Complexity:** $O(1)$ time and $O(1)$ auxiliary space.

#### Pitfalls
- Confusing a variable's value with its rate of change.
- Substituting values before differentiating a related-rates equation.
- Using a tangent-line approximation too far from its base point.
- Treating a first-order approximation as exact.
- Ignoring units.

---

## Lesson 6 — Mean Value Theorem and Curve Sketching

**Priority:** CORE  
**Core idea:** Connect average and instantaneous rates; use derivatives to understand where a function rises, falls, and bends.  
**Why it matters for a Quant Researcher:** Derivative tests support optimization, model diagnostics, and interpretation of how an objective or risk measure behaves.

### 6.1 Intuition

The Mean Value Theorem (MVT) says that, under specific conditions, there is at least one point where the instantaneous slope equals the average slope over an interval.

**Hinglish:** Agar poori journey ka average speed 60 km/h hai, toh suitable smoothness conditions mein journey ke beech kisi instant par speed exactly 60 km/h honi chahiye.

### 6.2 Mean Value Theorem

If:
1. $f$ is continuous on the closed interval $[a, b]$, and
2. $f$ is differentiable on the open interval $(a, b)$,

then at least one $c \in (a, b)$ exists such that:

$$\boxed{f'(c) = \frac{f(b) - f(a)}{b - a}}$$

- Right side: average rate of change / secant slope.
- Left side: instantaneous rate of change / tangent slope.

#### Worked example — $f(x) = x^2$ on $[1, 3]$

Endpoint values:

$$f(1) = 1, \qquad f(3) = 9$$

Average slope:

$$\frac{9 - 1}{3 - 1} = \frac{8}{2} = 4$$

Derivative:

$$f'(x) = 2x$$

Set instantaneous slope equal to average slope:

$$2c = 4 \implies \boxed{c = 2}$$

Since $2 \in (1, 3)$, this satisfies the MVT conclusion.

#### When MVT cannot be applied
For $f(x) = |x|$ on $[-1, 1]$, the function is continuous on the closed interval but not differentiable at $x = 0$. The MVT conditions fail, so the theorem cannot be invoked.

**Remember:** A theorem's assumptions are part of the theorem. Do not use its conclusion without checking them.

### 6.3 First derivative — increasing and decreasing

- $f'(x) > 0$: function is increasing.
- $f'(x) < 0$: function is decreasing.
- $f'(x) = 0$: stationary point candidate.

A critical number can occur where $f'(x) = 0$, or where $f'$ does not exist while $f$ is defined.

A stationary point is **not automatically** a local maximum or minimum.

### 6.4 First Derivative Test

Check the sign of $f'$ immediately to the left and right of a critical point.

| Sign before | Sign after | Classification |
| :--- | :--- | :--- |
| $(+)$ | $(-)$ | Local maximum |
| $(-)$ | $(+)$ | Local minimum |
| $(+)$ | $(+)$ | Neither, based on this test |
| $(-)$ | $(-)$ | Neither, based on this test |

**Hinglish memory trick:**
- Positive se negative = pehle upar, phir neeche = maximum.
- Negative se positive = pehle neeche, phir upar = minimum.

### 6.5 Second derivative — concavity

- $f''(x) > 0$: concave up; the slope is increasing.
- $f''(x) < 0$: concave down; the slope is decreasing.

A possible inflection point occurs where concavity changes. Merely finding $f''(x) = 0$ is not enough; check the sign of $f''$ on both sides.

**Important distinction:**
- First derivative tells direction / monotonicity.
- Second derivative tells how the slope changes / concavity.

### 6.6 Worked example A — quadratic minimum

Let:

$$f(x) = x^2 - 4x + 3$$

First derivative:

$$f'(x) = 2x - 4$$

Stationary point:

$$2x - 4 = 0 \implies x = 2$$

Second derivative:

$$f''(x) = 2 > 0$$

Therefore the function is concave up and has a local minimum at $x = 2$.

$$f(2) = 4 - 8 + 3 = -1$$

$$\boxed{\text{Local minimum at } (2, -1)}$$

### 6.7 Worked example B — cubic maximum and minimum

Let:

$$f(x) = x^3 - 3x$$

First derivative:

$$f'(x) = 3x^2 - 3 = 3(x - 1)(x + 1)$$

Critical points:

$$3(x - 1)(x + 1) = 0 \implies \boxed{x = -1,\; 1}$$

Sign analysis:

| Interval | Sign of $f'(x)$ | Behavior |
| :--- | :--- | :--- |
| $x < -1$ | $(+)$ | Increasing |
| $-1 < x < 1$ | $(-)$ | Decreasing |
| $x > 1$ | $(+)$ | Increasing |

Therefore:
- At $x = -1$, $(+ \to -)$: local maximum.
- At $x = 1$, $(- \to +)$: local minimum.

Function values:

$$f(-1) = 2, \qquad f(1) = -2$$

$$\boxed{\text{Local maximum } (-1, 2)}$$

$$\boxed{\text{Local minimum } (1, -2)}$$

### 6.8 Python — plot a function and its derivative

```python
import numpy as np
import matplotlib.pyplot as plt

x = np.linspace(-3, 3, 400)

# Function and analytical first derivative
f = x**3 - 3*x
fp = 3*x**2 - 3

plt.plot(x, f, label="f(x) = x^3 - 3x")
plt.axhline(0)
plt.grid(True)
plt.xlabel("x")
plt.ylabel("f(x)")
plt.legend()
plt.show()

plt.plot(x, fp, label="f'(x) = 3x^2 - 3")
plt.axhline(0)
plt.grid(True)
plt.xlabel("x")
plt.ylabel("f'(x)")
plt.legend()
plt.show()
```

**Complexity:** $O(n)$ time and $O(n)$ memory for $n$ grid points.

#### Pitfalls
- $f'(x) = 0$ does not guarantee an extremum.
- Do not confuse first derivative with second derivative.
- $f''(x) = 0$ does not by itself prove an inflection point.
- A graph is useful for intuition, but verify conclusions analytically.
- MVT requires continuity on $[a, b]$ and differentiability on $(a, b)$.

---

## Lesson 7 — Applications of Calculus

**Priority:** CORE  
**Core idea:** Use derivatives to optimize objectives and quantify marginal effects.  
**Why it matters for a Quant Researcher:** Optimization and sensitivity are used in portfolio construction, execution, pricing, risk, and economic modeling.

### 7.1 Intuition

A derivative measures a marginal change. Optimization asks where an objective reaches its highest or lowest value, subject to the problem's constraints.

**Hinglish:** Trading ya business mein hum poochte hain: quantity kitni honi chahiye, cost kaise control ho, profit maximum kahan ho, aur price badalne par demand kitni badlegi?

### 7.2 Optimization workflow

For a differentiable objective $f(x)$:

1. Define the objective and decision variable.
2. Identify the feasible domain and constraints.
3. Calculate $f'(x)$.
4. Solve $f'(x) = 0$ for stationary candidates.
5. Also inspect endpoints and points where the derivative does not exist.
6. Classify candidates using derivative tests or direct comparison.
7. Check feasibility and interpretation.

#### Second Derivative Test
At a stationary point $x^*$, where $f'(x^*) = 0$:
- If $f''(x^*) < 0$: local maximum.
- If $f''(x^*) > 0$: local minimum.
- If $f''(x^*) = 0$: test is inconclusive; use another method.

A local maximum is not automatically a global maximum. For a closed bounded feasible interval, compare all relevant candidates and endpoints.

### 7.3 Revenue, cost, and profit

$$\pi(q) = R(q) - C(q)$$

Where:
- $R(q)$: revenue.
- $C(q)$: cost.
- $\pi(q)$: profit.
- $q$: output quantity.

Marginal revenue and marginal cost:

$$MR = R'(q), \qquad MC = C'(q)$$

For an interior differentiable profit optimum:

$$\pi'(q) = 0$$

$$R'(q) - C'(q) = 0$$

$$\boxed{MR = MC}$$

This is a first-order candidate condition. Check second-order conditions, boundaries, and feasibility.

#### Worked example — find profit-maximizing quantity

Suppose:

$$R(q) = 100q - 2q^2$$

$$C(q) = 20q + q^2$$

Marginal revenue:

$$MR = 100 - 4q$$

Marginal cost:

$$MC = 20 + 2q$$

Set $MR = MC$:

$$100 - 4q = 20 + 2q$$

$$80 = 6q$$

$$\boxed{q^* = \frac{80}{6} \approx 13.333}$$

Profit function:

$$\pi(q) = R(q) - C(q) = 80q - 3q^2$$

Second derivative:

$$\pi''(q) = -6 < 0$$

Thus the stationary point is a maximum for this unconstrained quadratic model. Real problems may impose integer, capacity, or other constraints.

### 7.4 Price elasticity of demand

Elasticity measures percentage responsiveness of quantity demanded to price:

$$\boxed{E = \frac{dQ}{dP}\frac{P}{Q}}$$

Interpretation by magnitude:
- $|E| > 1$: elastic.
- $|E| < 1$: inelastic.
- $|E| = 1$: unit elastic.

For a conventional downward-sloping demand curve, elasticity is usually negative. The sign indicates direction; the magnitude indicates responsiveness.

#### Worked example

Given:

$$Q = 100, \quad P = 20, \quad \frac{dQ}{dP} = -10$$

$$E = -10\left(\frac{20}{100}\right)$$

$$\boxed{E = -2}$$

Since $|E| = 2 > 1$, demand is elastic.

Interpretation: locally, a $1\%$ increase in price is associated with approximately a $2\%$ decrease in quantity demanded, holding the model specification and other factors fixed.

### 7.5 Option Omega — option elasticity

Option Omega measures the percentage sensitivity of option value to a percentage change in the underlying:

$$\boxed{\Omega = \frac{\Delta S}{V}}$$

Where:
- $\Delta$: option Delta.
- $S$: underlying price.
- $V$: option value.

An Omega of $6$ means that, locally, a $1\%$ change in the underlying corresponds to approximately a $6\%$ change in option value, all else held fixed.

This is a local sensitivity, not a guaranteed realized return. Gamma, volatility changes, time decay, rates, dividends, spreads, and execution costs affect actual P&L.

### 7.6 Quant-finance applications

- **Portfolio construction:** optimize return/risk objectives subject to constraints.
- **Execution:** balance market impact, spread, timing, and opportunity costs.
- **Options:** Greeks measure local sensitivities; higher-order terms improve approximations.
- **Research:** marginal effects help interpret models, but statistical significance and economic/trading significance must be evaluated separately.

### 7.7 Python — grid-search profit maximum

```python
import numpy as np

def revenue(q):
    return 100*q - 2*q**2

def cost(q):
    return 20*q + q**2

def profit(q):
    return revenue(q) - cost(q)

# Evaluate profit on a grid of feasible quantities
q = np.linspace(0, 30, 301)
profits = profit(q)

best_index = np.argmax(profits)
best_q = q[best_index]
best_profit = profits[best_index]

print("Approximate best quantity:", best_q)
print("Approximate maximum profit:", best_profit)
```

**Complexity:** $O(n)$ time and $O(n)$ memory for $n$ grid points.

This grid search is numerical. The analytical derivative gives the exact stationary candidate for the specified quadratic model. Grid resolution can affect the reported numerical optimum.

#### Pitfalls
- A stationary point may be a minimum or neither.
- Ignoring constraints can produce an infeasible solution.
- A local optimum is not always global.
- A model optimum is not automatically a tradable optimum.
- Include transaction costs, liquidity, risk, capacity, and uncertainty.
- Do not interpret a local sensitivity as a forecast or guaranteed return.

---

## Lesson 8 — The Integral

**Priority:** CORE  
**Core idea:** Integration accumulates a rate or adds up infinitesimal contributions over an interval.  
**Why it matters for a Quant Researcher:** Integration appears in cumulative P&L, probability, expected values, continuous-time models, and derivative pricing.

### 8.1 Intuition — accumulation

A derivative describes an instantaneous rate of change. An integral accumulates that rate over an interval.

$$\boxed{\text{Rate} \xrightarrow{\text{integrate}} \text{Accumulated change}}$$

**Hinglish:** Derivative batata hai ki kisi instant par change kitni speed se ho raha hai. Integral batata hai ki poore interval mein total kitna change jama hua.

### 8.2 Indefinite integral — antiderivative

If $F'(x) = f(x)$, then:

$$\boxed{\int f(x)\,dx = F(x) + C}$$

$C$ is the constant of integration because the derivative of every constant is zero.

#### Power Rule for integration

For $n \ne -1$:

$$\boxed{\int x^n\,dx = \frac{x^{n+1}}{n+1} + C}$$

Example:

$$\int 6x^2\,dx = 6\left(\frac{x^3}{3}\right) + C$$

$$\boxed{= 2x^3 + C}$$

Important exception:

$$\boxed{\int \frac{1}{x}\,dx = \ln|x| + C}$$

The power rule formula cannot be used at $n = -1$, because it would divide by zero.

### 8.3 Definite integral

A definite integral has lower and upper limits and gives a numerical signed accumulation:

$$\boxed{\int_a^b f(x)\,dx = F(b) - F(a)}$$

This is the evaluation form of the Fundamental Theorem of Calculus, assuming the required continuity and antiderivative conditions.

#### Worked example

$$\int_1^3 4x\,dx$$

Antiderivative:

$$F(x) = 2x^2$$

Apply limits:

$$\Big[2x^2\Big]_1^3 = 2(3^2) - 2(1^2)$$

$$= 18 - 2$$

$$\boxed{16}$$

#### Definite vs indefinite integral

| Indefinite integral | Definite integral |
| :--- | :--- |
| No limits | Has lower and upper limits |
| Gives a family of antiderivatives | Gives a numerical signed accumulation |
| Includes $+C$ | Do not add a free $+C$ to the final evaluated number |
| Example: $\int 2x\,dx = x^2 + C$ | Example: $\int_0^5 2x\,dx = 25$ |

### 8.4 Fundamental Theorem of Calculus — two key ideas

#### Part 1 — differentiation of accumulated area
If:

$$G(x) = \int_a^x f(t)\,dt$$

and $f$ is continuous, then:

$$\boxed{G'(x) = f(x)}$$

Meaning: the derivative of accumulated area recovers the original rate.

#### Part 2 — evaluating a definite integral
If $F'(x) = f(x)$, then:

$$\boxed{\int_a^b f(x)\,dx = F(b) - F(a)}$$

Meaning: find an antiderivative, then subtract its value at the lower limit from its value at the upper limit.

### 8.5 Signed area

A definite integral is **signed** area:
- Function above the $x$-axis contributes positively.
- Function below the $x$-axis contributes negatively.

A negative definite integral does not mean the function is negative everywhere. It means the net signed area below the axis outweighs the area above it.

If geometric area is required, use absolute values or split the interval at sign changes:

$$\text{Geometric area} = \int_a^b |f(x)|\,dx$$

### 8.6 Rate versus accumulated P&L — crucial data distinction

If continuous P&L rate is:

$$r(t) = \frac{dP}{dt}$$

then total P&L change from time $0$ to time $T$ is:

$$\boxed{P(T) - P(0) = \int_0^T r(t)\,dt}$$

#### Worked example — variable P&L rate

Suppose:

$$r(t) = 2t, \qquad 0 \le t \le 3$$

Accumulated change:

$$\int_0^3 2t\,dt = \Big[t^2\Big]_0^3$$

$$= 9 - 0$$

$$\boxed{9}$$

But the instantaneous rate at minute $3$ is:

$$r(3) = 6$$

Therefore:
- $r(3) = 6$: rate at exactly minute $3$.
- $\int_0^3 r(t)\,dt = 9$: accumulated change over the full interval.

#### Which operation should trading data use?

| What the dataset contains | Correct operation |
| :--- | :--- |
| Minute-wise incremental P&L changes ($\Delta P_i$), in currency | Direct sum: $\sum_i \Delta P_i$ |
| P&L rate $r(t)$, in currency/minute | Integrate rate over time: $\int r(t)\,dt$ |
| P&L rate sampled at discrete timestamps | Numerical integration estimates accumulation |
| Cumulative P&L series | Final cumulative P&L minus initial cumulative P&L, if the series is defined consistently |

**Unit check:** $\text{Currency/minute} \times \text{minutes} = \text{currency}$.

**Do not confuse:** A P&L rate is not the same thing as a P&L increment. If minute-wise changes are already provided, summing them is normally the correct operation. Do not integrate those increments again.

### 8.7 Riemann sums — rectangles approximate area

Divide $[a, b]$ into $n$ subintervals. For equal-width intervals:

$$\Delta t = \frac{b - a}{n}$$

Choose a sample point $t_i^*$ in each interval. The Riemann sum is:

$$\boxed{\sum_{i=1}^{n} f(t_i^*)\,\Delta t}$$

Under suitable integrability conditions:

$$\boxed{\int_a^b f(t)\,dt = \lim_{n \to \infty} \sum_{i=1}^{n} f(t_i^*)\,\Delta t}$$

**Hinglish:** Pehle bade rectangles se area estimate karte hain. Intervals ko chhota aur rectangles ko zyada karte jaate hain. Suitable conditions mein limit exact integral tak pahunchti hai.

#### Worked example — $f(t) = 2t$ on $[0, 2]$

Exact integral:

$$\int_0^2 2t\,dt = 4$$

**Two right-endpoint rectangles:**

$$\Delta t = 1, \qquad t_i^* = 1, 2$$

$$[2(1)](1) + [2(2)](1) = 2 + 4 = \boxed{6}$$

**Four right-endpoint rectangles:**

$$\Delta t = 0.5, \qquad t_i^* = 0.5, 1, 1.5, 2$$

Function values are $1, 2, 3, 4$:

$$(1 + 2 + 3 + 4)(0.5) = \boxed{5}$$

The estimates move toward the exact value $4$. Since the function is increasing, right-endpoint rectangles overestimate the area.

### 8.8 Trapezoidal Rule — numerical integration

Instead of using a rectangle, approximate the function between two adjacent observations with a straight line. The area is a trapezoid:

$$\boxed{A_i \approx \frac{f(t_i) + f(t_{i+1})}{2}(t_{i+1} - t_i)}$$

For all intervals:

$$\boxed{\int_a^b f(t)\,dt \approx \sum_{i=0}^{n-1} \frac{f(t_i) + f(t_{i+1})}{2}\,\Delta t_i}$$

where:

$$\Delta t_i = t_{i+1} - t_i$$

Use the actual interval width for irregular timestamps.

#### Worked example A — straight-line rate

For $f(t) = 2t$ on $[0, 2]$, observations at $t = 0, 1, 2$:

Interval $0\text{–}1$:

$$A_1 = \frac{0 + 2}{2}(1) = 1$$

Interval $1\text{–}2$:

$$A_2 = \frac{2 + 4}{2}(1) = 3$$

Total:

$$\boxed{1 + 3 = 4}$$

This is exact because the function is linear.

#### Worked example B — curved function

For $f(t) = t^2$ on $[0, 2]$, using one trapezoid:

$$A_{\text{trap}} = \frac{0 + 4}{2}(2) = 4$$

Exact integral:

$$\int_0^2 t^2\,dt = \left[\frac{t^3}{3}\right]_0^2 = \frac{8}{3} \approx 2.667$$

So one trapezoid gives an approximation, not the exact answer. More intervals often improve the estimate, but accuracy depends on curvature and sampling.

### 8.9 Worked trading-data example

Suppose observed P&L rates are:

| Time (minute) | P&L rate (₹/minute) |
| :---: | :---: |
| 0 | 4 |
| 1 | 8 |
| 2 | 12 |

Assume linear interpolation between observations.

Interval $0\text{–}1$:

$$A_1 = \frac{4 + 8}{2}(1) = 6$$

Interval $1\text{–}2$:

$$A_2 = \frac{8 + 12}{2}(1) = 10$$

Total:

$$\boxed{P_{\text{change}} \approx ₹16}$$

Because these observations lie on a straight line, the trapezoidal result is exact for that assumed linear path. The actual unobserved path between observations is not known merely from the samples.

### 8.10 Python — trapezoidal integration from scratch

```python
time = [0, 1, 2]
rate = [4, 8, 12]  # currency per minute

total = 0.0

for i in range(len(time) - 1):
    # Actual time difference; works with irregular intervals too
    dt = time[i + 1] - time[i]

    # Average endpoint rate multiplied by interval width
    area = (rate[i] + rate[i + 1]) / 2 * dt

    total += area

print("Estimated accumulated P&L:", total)
# Estimated accumulated P&L: 16.0
```

**Complexity:** $O(n)$ time for $n$ observations; $O(1)$ extra working memory, excluding the input arrays.

### 8.11 Python — NumPy and SciPy

#### NumPy for sampled observations

```python
import numpy as np

time = np.array([0, 1, 2])
rate = np.array([4, 8, 12])

estimated_total = np.trapezoid(rate, x=time)
print(estimated_total)  # 16.0
```

#### SciPy for a known continuous function

```python
from scipy.integrate import quad

def pnl_rate(t):
    return 2 * t

total, estimated_error = quad(pnl_rate, 0, 3)

print("Integral:", total)  # 9.0
print("Estimated numerical error:", estimated_error)
```

`quad` uses adaptive numerical quadrature. Its error output is an estimate of numerical integration error, not an estimate of market-data quality or model correctness.

### 8.12 Quant research pitfalls

- Sum incremental P&L; do not integrate increments again.
- Integrate a rate only after confirming its units.
- Use actual timestamp differences for irregularly spaced observations.
- Check missing timestamps, duplicate rows, market breaks, and outliers.
- Trapezoidal integration assumes linear interpolation between adjacent observations.
- Numerical integration error and market-data error are different.
- A correct cumulative P&L calculation does not prove that a strategy has alpha.
- Include transaction costs, slippage, fees, and execution assumptions when evaluating strategy P&L.

---

## Master Cheat Sheet — Lessons 5 to 8

### A. Formula sheet

| Concept | Formula | What it tells you |
| :--- | :--- | :--- |
| Related rates | $\frac{dy}{dt} = \frac{dy}{dx}\frac{dx}{dt}$ | How a change in one variable drives another over time |
| Linear approximation | $L(x) = f(a) + f'(a)(x - a)$ | Nearby value using tangent line |
| First-order change | $\Delta f \approx f'(x)\,\Delta x$ | Local sensitivity |
| MVT | $f'(c) = \frac{f(b) - f(a)}{b - a}$ | Some tangent slope equals the secant slope |
| Increasing | $f'(x) > 0$ | Function rises |
| Decreasing | $f'(x) < 0$ | Function falls |
| Local maximum test | $f': + \to -$ | Increasing then decreasing |
| Local minimum test | $f': - \to +$ | Decreasing then increasing |
| Concave up | $f''(x) > 0$ | Slope is increasing |
| Concave down | $f''(x) < 0$ | Slope is decreasing |
| Second derivative test | $f' = 0,\; f'' < 0$ max; $f'' > 0$ min | Classifies a stationary point locally |
| Profit | $\pi(q) = R(q) - C(q)$ | Revenue minus cost |
| Marginal revenue | $MR = R'(q)$ | Extra revenue per marginal unit |
| Marginal cost | $MC = C'(q)$ | Extra cost per marginal unit |
| Interior profit candidate | $MR = MC$ | First-order condition |
| Price elasticity | $E = \frac{dQ}{dP}\frac{P}{Q}$ | Percentage responsiveness of quantity to price |
| Option Omega | $\Omega = \frac{\Delta S}{V}$ | Local percentage sensitivity of option value to underlying |
| Indefinite integral | $\int f(x)\,dx = F(x) + C$ | Family of antiderivatives |
| Power integration rule | $\int x^n\,dx = \frac{x^{n+1}}{n+1} + C,\; n \ne -1$ | Antiderivative of a power |
| Log exception | $\int \frac{1}{x}\,dx = \ln|x| + C$ | Antiderivative of $1/x$ |
| Definite integral | $\int_a^b f(x)\,dx = F(b) - F(a)$ | Net signed accumulation |
| FTC Part 1 | $\frac{d}{dx}\int_a^x f(t)\,dt = f(x)$ | Derivative of accumulated area |
| Riemann sum | $\sum_{i=1}^n f(t_i^*)\,\Delta t$ | Rectangle-based accumulation estimate |
| Trapezoidal rule | $\sum_{i=0}^{n-1} \frac{f_i + f_{i+1}}{2}\,\Delta t_i$ | Piecewise-linear numerical integration |
| Discrete P&L | $\sum_i \Delta P_i$ | Add observed increments |
| Continuous-rate P&L | $\int_0^T r(t)\,dt$ | Accumulate a rate over time |

### B. Conditions and assumptions to memorize

#### Mean Value Theorem
- Continuous on $[a, b]$.
- Differentiable on $(a, b)$.

#### Second Derivative Test
- Must first have a stationary point: $f'(x^*) = 0$.
- $f''(x^*) < 0$: local maximum.
- $f''(x^*) > 0$: local minimum.
- $f''(x^*) = 0$: inconclusive.

#### Linear approximation
- Local approximation around $a$.
- Accuracy generally declines as you move farther from $a$.
- Requires differentiability at the expansion point; stronger smoothness supports stronger error control.

#### Trapezoidal rule
- Uses endpoint values and assumes a straight-line connection over each interval.
- Exact for a linear function on an interval.
- Generally approximate for curved functions.
- Use actual time widths when intervals are irregular.

### C. Five essential distinctions

| Do not confuse | Correct distinction |
| :--- | :--- |
| $f'(x)$ vs $f''(x)$ | Direction vs concavity |
| Stationary point vs extremum | $f' = 0$ is a candidate, not proof |
| Local vs global maximum | Local compares nearby points; global compares the full feasible domain |
| Indefinite vs definite integral | Antiderivative family vs numerical signed accumulation |
| P&L increment vs P&L rate | Sum increments; integrate rates |

### D. Three-line Hinglish revision

1. **Lesson 5:** Related rates linked quantities ki speed batate hain; linearization nearby value ka tangent-line estimate deta hai.
2. **Lessons 6–7:** First derivative direction batata hai, second derivative concavity; optimization mein stationary candidates ko classify karke constraints bhi check karte hain.
3. **Lesson 8:** Derivative rate hai, integral accumulation. Discrete P&L changes ko sum karo; continuous P&L rate ko integrate karo.

---

## Common Mistakes and Corrections

| Common mistake | Correct idea |
| :--- | :--- |
| Substituting values before differentiating a related-rates equation | Differentiate with respect to time first, then substitute instantaneous values |
| Assuming a tangent-line estimate is exact | It is a local approximation |
| Applying MVT without checking conditions | Check continuity on the closed interval and differentiability inside |
| Assuming $f'(x) = 0$ means maximum/minimum | Check derivative sign changes or use a valid classification test |
| Using $f''(x) = 0$ as proof of inflection | Verify that concavity changes |
| Calling every stationary point a turning point | A stationary point may be neither maximum nor minimum |
| Assuming $MR = MC$ proves a global optimum | It is a first-order candidate condition; check second order and boundaries |
| Ignoring the negative sign in demand elasticity | Sign gives direction; magnitude gives responsiveness |
| Forgetting $+C$ in an indefinite integral | Include the constant of integration |
| Adding $+C$ to a final definite-integral value | Evaluate upper minus lower limit; final result is a number |
| Assuming a negative integral means the function is always negative | It means net signed area is negative |
| Treating a finite Riemann sum as exact | It is an approximation unless special circumstances make it exact |
| Assuming trapezoidal rule is always exact | Exact for linear functions; generally approximate for curved functions |
| Integrating minute-wise P&L increments | Sum the increments directly |
| Ignoring irregular time intervals | Use each actual $\Delta t_i$ |

---

## Quant Research Connections

### 1. Sensitivity and Greeks
A derivative is a local sensitivity. Delta estimates the first-order effect of a small underlying-price move on option value. Gamma captures the change in Delta and contributes a second-order term.

### 2. Optimization and portfolio construction
Calculus helps derive candidate optima, but realistic portfolio problems require constraints, estimation uncertainty, transaction costs, and robust out-of-sample validation.

### 3. Marginal cost and execution
The $MR = MC$ idea illustrates balancing marginal benefit against marginal cost. Execution research similarly compares expected benefit against spread, impact, fees, and timing risk. The economic setup is different, but the marginal reasoning is related.

### 4. Integration and cumulative quantities
Integrating a rate produces an accumulated quantity. Examples include:
- P&L rate to cumulative P&L change.
- Probability density to probability over an interval.
- Marginal cost to total variable cost, given a boundary condition.
- Instantaneous flow to cumulative volume.

### 5. Theory versus market reality
Mathematics can calculate a sensitivity, optimum, or integral under stated assumptions. It cannot by itself establish:
- that a model is correctly specified;
- that data are free from leakage or survivorship bias;
- that a strategy has statistically robust alpha;
- that an apparent edge survives costs and execution;
- that a backtest will generalize out of sample.

Keep the research discipline: observation is not proof, statistical significance is not economic significance, and a failed hypothesis is still a valid research result.

---

## Active Recall Questions (No Solutions)

Attempt these without looking at the notes. Ask for hints or solutions only after making an attempt.

### Conceptual
1. Why do we differentiate a related-rates equation with respect to time before substituting the known instantaneous values?
2. State both assumptions required by the Mean Value Theorem.
3. Can a point with $f'(x) = 0$ fail to be a local maximum or minimum? Explain.
4. What is the difference between the information given by $f'(x)$ and $f''(x)$?
5. Why is $MR = MC$ not, by itself, a complete proof of a global profit maximum?
6. What does price elasticity of $-2$ mean in percentage terms?
7. Why does an indefinite integral include $+C$?
8. Why is a definite integral called signed accumulation?
9. Under what conditions does a Riemann sum converge to a definite integral?
10. What assumption does the trapezoidal rule make between two adjacent observations?

### Numerical
1. A circle has radius $r = 4$ and its radius increases at $dr/dt = 3$ units/second. Find $dA/dt$.
2. Use linearization of $f(x) = \sqrt{x}$ at $a = 100$ to estimate $\sqrt{102}$.
3. For $f(x) = x^2$ on $[0, 4]$, find the MVT point $c$.
4. Find and classify the stationary points of $f(x) = x^3 - 3x$.
5. If $R(q) = 80q - q^2$ and $C(q) = 10q + 2q^2$, find the interior stationary candidate for profit and classify it.
6. If $Q = 200,\; P = 50,\; dQ/dP = -4$, calculate price elasticity.
7. Evaluate $\int_0^2 3x^2\,dx$.
8. For rates $2$, $6$, and $10$ currency units/minute at times $0$, $1$, and $2$ minutes, calculate trapezoidal accumulated change.

### Coding
1. Write a Python function that calculates the trapezoidal integral for irregular timestamps. Expected input: `time=[0, 1, 3]`, `rate=[2, 4, 8]`. Expected output: `15.0`.
2. Write a Python function that evaluates profit over a feasible quantity grid and returns the best grid quantity and corresponding profit. State its time and space complexity.

---

## End of Notes

**Next syllabus topic:** Calculus II — Lesson 1: Advanced Integration Techniques.

Before moving forward, complete the active-recall questions and the prerequisite check. Do not confuse familiarity from reading with independent problem-solving ability.
calculus_1_lessons_5_to_8.md
Displaying calculus_1_lessons_5_to_8.md.