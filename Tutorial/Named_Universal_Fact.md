## Named Universal Fact

It is often we want to use a universal fact to check a specific fact. And we find that there are more parameters in the universal fact than the specific fact. For example:

```litex
know forall a, b, c R: a < b, b < c => a < c
let a, b, c R: a < b, b < c
# a < c # This does not work!
```

We can not prove `a < c` since we do not know which `b` is used by `forall a, b, c R: a < b, b < c => a < c` to prove `a < c`.

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

However, this is not the best way to do it. Litex provides you a short way to do it.

```litex
know @transitivity_of_less(a, b, c R):
    a < b
    b < c
    =>:
        a < c
```

The above example means:

```litex
prop transitivity_of_less(a, b, c R):
    a < b
    b < c

know forall a, b, c R: $transitivity_of_less(a, b, c) => a < c
```

