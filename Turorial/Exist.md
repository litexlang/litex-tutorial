# Exist

*Exist* is also a common conception.

## Claim a Exist Proposition

You can claim an Exist Proposition `larger_than`(For all `y` in `R` and `y > 0`, there exists `x` in `R` such that `x > y`):

```litex
exist_prop x R st larger_than(y R):
    dom:
        y > 0
    iff:
        x > y
```
`exist_prop` is the reserved word of Exist Proposition. `st` means *such that*. As you can see `exist_prop ... st ...` is a fixed match when you claim an Exist Proposition. 

Also, you can hide the `dom`:

```litex
exist_prop x R st larger_than(y R):
    y > 0
    iff:
        x > y
```

If you make `y` in `N_pos`, you can hide `iff`, too:

```litex
exist_prop x R st larger_than(y N_pos):
    x > y
```

## Prove claimed Exist Proposition

Every Exist Proposition have to be proved. Like what you usual do on math, You can just give an example with `exist`:

```litex
exist_prop x R st larger_than(y R):
    y > 0
    iff:
        x > y

let m N_pos

know exist m + 1 st $larger_than(m)
```

Or, you can just claim it's true on a specific set:

```litex
exist_prop x R st larger_than(y R):
    y > 0
    iff:
        x > y

know forall m N_pos:
    $larger_than(m)
```

## Call a Exist Proposition

Now, you may want to claim an Object which is satisfied this Exist Proposition. You should use `have ... st ...`:

```litex
exist_prop x R st larger_than(y R):
    y > 0
    iff:
        x > y

know forall y N_pos:
    $larger_than(y)

let m N_pos

have x st $larger_than(m)

x $in R
x > m
```

You claimed an Object `x` which is satisfied `larger_than(m)`. Still remember, ensure the Exist Proposition was proved before you call it, or you would get Error form Litex.