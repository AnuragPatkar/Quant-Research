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
