# Forall

Mathematics is fundamentally about deducing new facts from previously established ones. In particular, general statements can be used to derive specific instances.

The concept of for all is ubiquitous in both mathematics and the real world. In Litex, universal quantification is expressed with the forall keyword. Here is an example:

```litex
forall x N_pos:
    x $in N_pos
```

It reads: for all x in N_pos (the set of all positive natural numbers), x is in N_pos (the set of all positive natural numbers). This is always true, since the assumption (for all x in N_pos) is always true is just the same as the conclusion (x is in N_pos).

The complete syntax of forall is:

```
forall parameter1 set1, parameter2 set2, ...:
    domFact1
    domFact2
    ...
    =>:
        thenFact1
        thenFact2
        ...
```

It reads: forall parameter1 in set1, parameter2 in set2, ..., with assumption domFact1, domFact2, ..., satisfied, then conclusion thenFact1, thenFact2, ... is true. (Understand assumption as the required domain facts for the parameters)

`$in` here is a build-in Proposition for Litex users, which means the literal meaning *in*. You can also use it here like `$in(x, N_pos)` according to last chapter. So above lines claimed an obvious fact: for all `x` in `N_pos`, `x` in `N_pos`.

What should be like if we meet more complex situation like this fact: for all `x`, `y` in `R`, if `x > 0`, `y > 0`, then `x + y > 0`. This fact includes additional restriction, which could be expressed by Litex like:

```litex
know forall x, y R: x > 0, y > 0 => x + y > 0
```

To make claim lines less, you could hide some reserved word for some situation. For example, you could hide `dom`:

```litex
forall x R:
    x > 0
    y > 0
    =>:
        x + y > 0
```

If you claim `x` in `N_pos` (the set of positive natural numbers) in the first line, there is no `dom` anymore. Then, you could hide `iff`.So, standard code of the example at the beginning of this chapter should be like:

```litex
forall x N_pos:
    =>:
        x $in R
```

Sometimes, you may want to claim two **equivalent** facts caused by the same restriction. You can add an `iff` after `then` block:

```litex
forall x R:
    dom:
        x > 1
    =>:
        x <= 2
    iff:
        not x > 2
```

> Note: Above format support fact_1 <=> fact_2 only. Two facts must be **equivalent**