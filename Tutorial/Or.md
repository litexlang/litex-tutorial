# Or

Or represents an inclusive disjunction, meaning at least one of the conditions is true. You can use it like:

```litex
let x R: x = 1

or:
    x = 1
    x = 2

or(x = 1, x = 2)
```

You can write specific facts under `or` facts, but you can not write `or` fact and `forall` fact under `or`.

`or` facts can be written in `forall` facts:

```litex
let s set, a s: forall x s => or(x = 1, x = 2); not a = 1
a = 2
```

`or` can also appear as dom of a `forall` fact

```litex
know forall x R: or(x = 1, x = 2) => x < 3
```