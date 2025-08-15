# Example Set 1

Examples are essential for effective learning. Run and write the following codes yourself so that you can use Litex better.

## Situations where named forall statements are useful

```litex
know forall a, b, c R: a < b, b < c => a < c
let a, b, c R: a < b, b < c
# a < c # This does not work!
```

If you run `a < c`, you will get an unknown. This is because Litex uses `match and substitution` to use known facts to check if a new statement is true. In this case, we do not know which `b` is used by `forall a, b, c R: a < b, b < c => a < c` to prove `a < c`, so `a < c` still can not be proved.

So how do we express: It is known as axiom (definition of `<`) that for all `a`, `b`, `c` in `R`, if `a < b` and `b < c`, then `a < c`?

It turns out we can give a name to the forall statement by defining a new proposition.

```litex
prop transitivity_of_less(a, b, c R):
    a < b
    b < c
    <=>:
        a < c

know forall a, b, c R: a < b, b < c => $transitivity_of_less(a, b, c)

let a, b, c R: a < b, b < c
$transitivity_of_less(a, b, c)
a < c
```

