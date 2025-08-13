# Introduction

## Words from the creator

Hi, I am Jiachen Shen, a hacker and creator of Litex. It is a computer language for formalizing reasoning. Computation is how math is used to solve real-world problems. Reason is how we enriches our understanding of the world. Such knowledge is precious because it can be mechanically verified by a given set of rules. Math, physics, computer science all rely on such strictness. The software industry has already revolutionized how we compute, and Litex is here to change how we reason.

A good art is what makes its creator happy and makes its users find it useful.[^1] I hope Litex can be a good art for both me and its users.

## What is Litex

Litex(/lɪ'tɛks/) is an intuitive and scalable formal language for coding your reasoning. The name is inspired by the combination of two computer languages that has huge impact on Litex: Lisp and TeX. It was created by Jiachen Shen in 2024, and has now become a community-driven project for everyone.

Since a 10-year-old can reason about basic math, even a 10-year-old should be able to learn and use Litex easily to solve their own problems. We assume a man without any math or programming background can learn Litex in 1-2 hours. 

Just like all successful programming languages, Litex aims to give users a sense of pleasure while using it, and to pragmatically solve the problems they face. The specific problem Litex addresses is: scaling formal reasoning in the AI age. This simplicity and accessibility of Litex reduces the time ratio, between formalizing a proof and writing it in natural language, from 10:1 to 1:1. That is why constructing Litex codebase is 10x cheaper and has a 10x lower entrance barrier than traditional formal languages (e.g. Lean, Coq, Isabelle, etc.). This is a blessing for both AI industry and math community.

## How to read this tutorial

The biggest strength of Litex is its intuitiveness. In the ideal case, we hope users can read and use Litex without having to learn it at all! 

The purpose of this slim tutorial is:

1. To record the most basic Litex syntax and keywords, ensuring there is no ambiguity for users.
2. To provide some examples for beginners to reference.

Please don’t feel any pressure when reading this tutorial — Litex is truly very simple.

The best way to learn Litex is to try writing the examples from the tutorial yourself, or translate the mathematics (or reasoning) you care about into Litex.

## Intuitive

Litex support all common expression in math like numbers, variables, functions, etc. 

Here is an example: to determine the correctness of solution of multivariate linear equation: 2x + 3y = 10, 4x + 5y = 14:

```litex
let x R, y R:
    2 * x + 3 * y = 10
    4 * x + 5 * y = 14
2 * (2 * x + 3 * y) = 2 * 10
4* x + 6 * y = 2 * 10
(4*x + 6 * y) - (4*x + 5 * y) = 2 * 10 - 14
(4*x + 6 * y) - (4*x + 5 * y) = y
y  = 6
2 * x + 3 * 6 = 10
2 * x + 18 - 18 = 10 - 18
2 * x + 18 - 18 = -8
(2 * x) / 2 = -8 / 2
(2 * x) / 2 = x
x = -4
```

Anyone can understand the above code. There is almost zero difference between how we write math and how we write Litex. However, traditional formal languages like Lean requires you to learn a lot of complicated syntax and concepts. Here is the comparison of the same example in Lean:

<table style="border-collapse: collapse; width: 100%; font-size: 12px">
  <tr>
    <th style="border: 2px solid black; padding: 4px; text-align: left; width: 50%;">Litex</th>
    <th style="border: 2px solid black; padding: 4px; text-align: left; width: 50%;">Lean 4</th>
  </tr>
  <tr>
    <td style="border: 2px solid black; padding: 2px; line-height: 1.5">
      <code>let x R, y R:</code><br>
      <code>&nbsp;&nbsp;2 * x + 3 * y = 10</code><br>
      <code>&nbsp;&nbsp;4 * x + 5 * y = 14</code><br><br>
      <code>2 * (2 * x + 3 * y) = 2 * 10</code><br>
      <code>4* x + 6 * y = 2 * 10</code><br>
      <code>(4*x + 6 * y) - (4*x + 5 * y) = 2 * 10 - 14</code><br>
      <code>(4*x + 6 * y) - (4*x + 5 * y) = y</code><br>
      <code>y = 6</code><br>
      <code>2 * x + 3 * 6 = 10</code><br>
      <code>2 * x + 18 - 18 = 10 - 18</code><br>
      <code>2 * x + 18 - 18 = -8</code><br>
      <code>(2 * x) / 2 = -8 / 2</code><br>
      <code>(2 * x) / 2 = x</code><br>
      <code>x = -4</code>
    </td>
    <td style="border: 2px solid black; padding: 2px; line-height: 1.5">
      <code>import Mathlib.Tactic</code><br><br>
      <code>example (x y : ℝ) (h₁ : 2 * x + 3 * y = 10) (h₂ : 4 * x + 5 * y = 14) : x = -4 ∧ y = 6 := by</code><br>
      <code>&nbsp;&nbsp;have h₃ : 2 * (2 * x + 3 * y) = 2 * 10 := by rw [h₁]</code><br>
      <code>&nbsp;&nbsp;have h₄ : 4 * x + 6 * y = 20 := by linear_combination 2 * h₁</code><br>
      <code>&nbsp;&nbsp;have h₅ : (4 * x + 6 * y) - (4 * x + 5 * y) = 20 - 14 := by</code><br>
      <code>&nbsp;&nbsp;rw [h₄, h₂]</code><br>
      <code>&nbsp;&nbsp;have h₆ : (4 * x + 6 * y) - (4 * x + 5 * y) = y := by</code><br>
      <code>&nbsp;&nbsp;ring</code><br>
      <code>&nbsp;&nbsp;have h₇ : 20 - 14 = 6 := by norm_num</code><br>
      <code>&nbsp;&nbsp;have h₈ : y = 6 := by</code><br>
      <code>&nbsp;&nbsp;rw [←h₆, h₅, h₇]</code><br>
      <code>&nbsp;&nbsp;have h₉ : 2 * x + 3 * 6 = 10 := by rw [h₈, h₁]</code><br>
      <code>&nbsp;&nbsp;have h₁₀ : 2 * x + 18 = 10 := by</code><br>
      <code>&nbsp;&nbsp;rw [mul_add] at h₉</code><br>
      <code>&nbsp;&nbsp;simp at h₉</code><br>
      <code>&nbsp;&nbsp;exact h₉</code><br>
      <code>&nbsp;&nbsp;have h₁₁ : 2 * x = -8 := by</code><br>
      <code>&nbsp;&nbsp;linear_combination h₁₀ - 18</code><br>
      <code>&nbsp;&nbsp;have h₁₂ : x = -4 := by</code><br>
      <code>&nbsp;&nbsp;linear_combination h₁₁ / 2</code><br>
      <code>&nbsp;&nbsp;exact ⟨h₁₂, h₈⟩</code>
    </td>
  </tr>
</table>


## Simple

Litex is more align with the expression habits of natural language. Reserved word of Litex is derived from commonly used mathematical logic expressions. 

Here is an example: to prove sqrt(2) is irrational:

```litex
fn logBase(x, y N) N:
    dom:
        x != 0

know forall x, y, z N:
    logBase(z, x^y) = y * logBase(z, x)
    logBase(z, x*y) = logBase(z, x) + logBase(z, y)

know forall x N:
    x != 0
    then:
        logBase(x, x) = 1

claim:
    not sqrt(2) $in Q
    prove_by_contradiction:
        have x, y st $rational_number_representation_in_fraction(sqrt(2))
        
        x = sqrt(2) * y

        x ^ 2 = (sqrt(2) ^ 2) * (y ^ 2)
        sqrt(2) ^ 2 = 2
        x ^ 2 = 2 * (y ^ 2)
        logBase(2, x ^ 2) = logBase(2, 2 * (y ^ 2))
        
        logBase(2, x ^ 2) = 2 * logBase(2, x)
        logBase(2, y ^ 2) = 2 * logBase(2, y)

        logBase(2, 2 * (y ^ 2)) = logBase(2, 2) + logBase(2, y ^ 2)
        logBase(2, 2) = 1
        logBase(2, 2 * (y ^ 2)) = 1 + logBase(2, y ^ 2)

        logBase(2, x ^ 2) = 1 + 2 * logBase(2, y)
        2 * logBase(2, x) = 1 + 2 * logBase(2, y)

        (2 * logBase(2, x)) % 2 = (1 + 2 * logBase(2, y)) % 2
        (2 * logBase(2, x)) % 2 = 0
        0 = (1 + 2 * logBase(2, y)) % 2

        (1 + 2 * logBase(2, y)) % 2 = 1 % 2 + (2 * logBase(2, y)) % 2
        1 % 2 + (2 * logBase(2, y)) % 2 = 1 + 0
        0 = 1
```

## Expressive

Litex built in all common conceptions of math such as set, proposition and others instead of make conceptions implemented via computer language.

Here is an example: to define a group, and prove R and Z are groups

```litex
prop is_group(s set, mul fn(s, s)s, inv fn(s)s, e s):
    forall x s, y s, z s:
        mul(mul(x, y), z) = mul(x, mul(y, z))
    forall x s:
        mul(x, inv(x)) = e
        mul(inv(x), x) = e

fn inverse(x R)R:
    inverse(x) + x = 0

forall x R:
    inverse(x) + x = 0
    x + inverse(x) = 0

forall x Z:
    x + inverse(x) = 0
    inverse(x) = -x
    -x $in Z
    inverse(x) $in Z

$is_group(R, +, inverse, 0)
$is_group(Z, +, inverse, 0)
```

[^1]: [Computer programming as an art](https://dl.acm.org/doi/10.1145/1283920.1283929)