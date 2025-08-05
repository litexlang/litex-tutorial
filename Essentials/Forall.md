# For all

*For all* is a common conception in math and even in real world. To express *for all* in Litex, we use `forall`:

```litex
forall x N_pos:
    x $in R
```

`$in` here is a build-in Proposition for Litex users, which means the literal meaning *in*. You can also use it here like `$in(x, R)` according to last chapter. So above lines claimed a obvious fact: for all `x` in `N_pos`, `x` in `R`.

What should be like if we meet more complex situation like this fact: for all `x`, `y` in `R`, if `x > 0`, `y > 0`, then `x + y > 0`. This fact includes additional restriction, which could be expressed by Litex like:

```litex
forall x, y R:
    dom:
        x > 0
        y > 0
    then:
        x + y > 0
```

Just like we add additional restriction on Proposition, we use `dom`! And as it should be, `dom` here could be hidden here as well:

```litex
forall x R:
    x > 0
    y > 0
    then:
        x + y > 0
```

You should have thought of it as well, the example at the beginning of this chapter is to hide the `then` because there is no `dom`! So, the default lines are:

```litex
forall x N_pos:
    then:
        x $in R
```

## 