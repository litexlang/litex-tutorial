# Proof

In long proof, You may use the same character to represent different concepts. You need `prove` to distinguish different proof part.

## Proof

`prove` provides a sub-environment that does not affect the part out of its sub-environment. In this case, `x` in different Prove block works individually:

```litex
prove:
    let x N_pos:
        x = 1
    or:
        x = 1
        x = 2

prove:
    let x R:
        not x < 0
    x >= 0

let x N:
    x = 0
x = 0
```

> Note: In this case, if you make claim of `let x N` before all Prove block, Litex would report an Error. Because you claimed `x` in parent-environment first and sub-environment would be affected.

## Claim

`prove` provide a individual part to show your sub-logic to readers. Litex won't use it to parent-environment. You can use `claim` to make something affect part out of the Prove sub-environment:

```litex
claim:
    @p(x N):
        x > 1
        then:
            x > -1
    prove:
        $larger_is_transitive(x, 1, -1)
        x > -1

let a N:
    a > 1
$p(a)
a > -1
```

`larger_is_transitive(x, y, z R)` is a built-in Proposition of Litex that means: x, y, z in R, x > y and y > z <=> x > z. You claimed a Proposition `p(x N)` in Claim block and prove it in Prove block. But you can still use it out of the sub-environment.

## Proof by Contradiction

`prove_by_contradiction` should always by used in Claim block. Here is a classical example, prove sqrt(2) is irrational using Proof by Contradiction:

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

## Proof in Each Case

`prove_in_each_case` should always be used with `or` together:

```litex
## TODO Provide a Litex-acceptable example
```

