# Prove by Contradiction

In math, one common way to prove a statement is to prove its negation is false. This method is called `Prove by Contradiction`.

```
claim:
    fact_you_want_to_prove
    prove_by_contradiction:
        statement1
        ...
        final_statement
```

`prove_by_contradiction` should always be used in `claim` block. In the environment of `prove_by_contradiction`, `not fact_you_want_to_prove` is assumed to be true. To make the process of proving by contradiction works, the `final_statement` should be a fact that is both true and false. After that, the assumption `not fact_you_want_to_prove` is false and `fact_you_want_to_prove` is true.

For example:

```litex
prop p(x R)
prop q(x R)
know forall x R: $p(x) => $q(x); not $q(1)
claim:
    not $p(1)
    prove_by_contradiction:
        $q(1) # is true, because $p(1) is assumed to be true
```