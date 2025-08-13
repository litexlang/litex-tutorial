# Introduction

## Words from the creator

Hi, I am Jiachen Shen, a hacker and creator of Litex. It is a computer language for formalizing reasoning. Computation is how math is used to solve real-world problems. Reason is how we enriches our understanding of the world. Such knowledge is precious because it can be mechanically verified by a given set of rules. Math, physics, computer science all rely on such strictness. The software industry has already revolutionized how we compute, and Litex is here to change how we reason.

A good art is what makes its creator happy and makes its users find it useful.[^1] I hope Litex can be a good art for both me and its users.

## What is Litex

Litex(/lɪ'tɛks/) is a simple and intuitive formal language.

## How to read this tutorial

The biggest strength of Litex is its intuitiveness. In the ideal case, we hope users can read and use Litex without having to learn it at all! 

The purpose of this slim tutorial is:

1. To record the most basic Litex syntax and keywords, ensuring there is no ambiguity for users.
2. To provide some examples for beginners to reference.

Please don’t feel any pressure when reading this tutorial — Litex is truly very simple.

The best way to learn Litex is to try writing the examples from the tutorial yourself, or translate the mathematics (or reasoning) you care about into Litex.

## Intuitive

Litex support all common express in math like numbers and calculation symbols. 

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