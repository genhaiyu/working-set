This note records how I built a factorization pipeline while solving a real problem in college algebra.

I did not start from theory.  
I started from a cubic polynomial that could not be factored using a single method.

The goal was simple:

- no guessing
- no dead ends
- no dependence on a "pretty" equation


## 1. Motivation

I needed a method that does not break halfway.

Grouping sometimes works.
It depends on how the expression is arranged.

Synthetic division is not used to finish the factorization.
Its role is to remove one power layer.
After that, only a quadratic remains.

The A/C method is limited.
It does not handle arbitrary leading coefficients well,
especially when they are not clean integers.

I wanted a process that keeps moving forward
until the factorization is finished.

## 2. Example Function

<figure>
	<img src="/units-img/polynomials/rational-polynomials-equation.png" alt="rational-polynomials-equation" style="width: 45%"/>
</figure>

I started with the example:

$g(x) = \frac{3x^3 - 4x^2 - 12x + 16}{5 - x}$

The task is to identify the intercepts and asymptotes, graph the rational function.

Before graphing, the numerator must be factored.

---

## 3. Standard Grouping Attempt

<figure>
	<img src="/units-img/polynomials/factor-by-grouping.png" alt="factor-by-grouping" style="width: 45%"/>
</figure>

I tried grouping first.

- Rearranging $3x^3 -12x -4x^2 + 16$
- Extracting common factors of $3x$ and $-4$
- Obtaining $(3x - 4)(x + 2)(x - 2)$

This works.

But this only works because the expression is clean.
It is a single-branch solution.

---

## 4. Why Grouping Is Not Enough

Grouping fails in many cases.

- Some cubics do not regroup cleanly
- Synthetic division requires a lucky guess
- Pattern recognition does not scale
- Leftover quadratics often appear

I did not want "a trick that works here".  
I wanted a method that works `in general`.

---

## 5. The Pipeline (General Algorithm)

<figure>
	<img src="/units-img/polynomials/universal-algorithm.png" alt="universal-algorithm" style="width: 45%"/>
</figure>

The solution was to combine several tools into one fixed sequence.

1. **Rational Root Test**  
   Generate possible rational roots from (constant ÷ leading-coef).

2. **Synthetic Division**  
   Test a candidate.  
   If it works, reduce the cubic.

3. **Quadratic Formula**  
   Solve the remaining quadratic directly.

4. **Leading-Coefficient Recovery**  
   Restore the original leading coefficient.

After this point, no guessing is required.

---

## 6. Execution on the Example

Steps:

1. Rational Root Test produces candidates:
   ±1, ±2, ±4, ±8, ±16, ...
2. Testing $(x = 2)$ works.
3. The remainder quadratic is $(3x^2 + 2x - 8)$.
4. Quadratic formula gives: $\frac 4 3$ and $-2$.
5. Recover the leading coefficient:

   $3(x- \frac 4 3)(x+2)$ → $(3x-4)(x+2)$

---

## 7. Why This Pipeline Does Not Fail

This process does not stop halfway.

- If a rational root exists, RRT will eventually hit it
- After one root is found, only a quadratic remains
- Quadratics do not require guessing
- Coefficient recovery preserves the original structure. It replaces the A/C method when the leading coefficient is not a clean integer.

Every branch returns to the same final factorization.

This is not a trick.
It is a controlled sequence.

---

## 8. Closing Notes

This was the first pipeline I built from college algebra tools.

- [Transferring `grouping method` into]
- ① possible rational roots test
- ② synthetic division
- ③ quadratic formula
- ④ coefficient recovery [into a `single algorithm`].

The point is not efficiency.
Each method must connect to the next.

This document is preserved as the first factorization pipeline I constructed by myself.