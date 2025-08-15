## Claim

Math is hard. It is important to organize your proof well. One way to do so is to divide a long proof into a series of independent sub-proofs and then combine them together. One way is using `claim` keyword.

```
claim:
    fact_you_want_to_prove
    prove:
        ....
```

The above statement works like this: Litex creates a sub-environment for `prove` block. In this sub-environment, all statements inside are executed. After all statements in `prove` block are executed, Litex will check if `fact_you_want_to_prove` is true. If it is, the proof is done. If it is not, Litex will report an Error. Then `fact_you_want_to_prove is true` will be added to the global environment. All statements in `prove` block does not affect the global environment.

For example

``` litex
exist_prop x N st p(y N):
    x > y

claim:
    $p(1)
    prove:
        let x N: x = 2
        2 > 1
        x > 1
        exist x st $p(1)
        $p(1)

$p(1) # true, because $p(1) is proved in the claim statement
# x = 2 is not visible out of the prove block, because x is declared in the prove block locally
```

You can use `claim` to make something affect part out of the Prove sub-environment:

```litex
claim:
    @p(x N):
        x > 1
        =>:
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

