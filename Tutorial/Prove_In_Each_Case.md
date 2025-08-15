# Proof in Each Case

If `or(fact1, fact2, ..., factN)` is true, `then_fact` is true in each case, then `then_fact` is always true. Litex uses `prove_in_each_case` to prove this kind of fact:

```
prove_in_each_case:
    or(fact1, fact2, ..., factN)
    =>:
        then_fact
    prove:
        # assume fact1 is true, prove then_fact
    prove:
        # assume fact2 is true, prove then_fact
    ...
    prove:
        # assume factN is true, prove then_fact
```

For example:
```litex
let x N: or(x = 1, x = 2)

prove_in_each_case:
    or(x = 1, x = 2)
    =>:
        x > 0
    prove:
        1 > 0
        x > 0
    prove:
        2 > 0
        x > 0
```