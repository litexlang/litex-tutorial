# Have

## Claim non-empty Set

You can claim a non-empty Set by enumerating all Objects in Set via `have set ... := {...}`:

```litex
have set s1 := {1, 2, 3}
```

Here, you claimed a finite Set `s1` with only 3 Objects: Number 1, Number 2 and Number 3.

Or you can claim a non-empty Set by add additional restrictions:

```litex
have set s2 := n N:
    n > 0
    n < 4
```

Here, you claimed a Set that containes elements in `N` and each element `n` must be larger than 0 and smaller than 4.

> Note: You may have a question: is `s2` different from `s1`? The answer is **yes**. `s1` is claimed by enumerating Objects, but `s2` is claimed by setting domain. Clearly, `s1` is a finite set but `s2` is not unless you proved there is only 1, 2 and 3 in the domain you set.

## Claim Object satisfied Exist Proposition

If you have claimed an [Exist Proposition](https://litexlang.org/doc/Turorial/Exist) and proved, you might want to claim an Object which is satisfied this Exist Proposition. You should use `have ... st ...`:

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

## Claim Objects in non-empty Set

You can claim an Object in built-in Set and use it:

```litex
have n N, z Z, q Q, r R, c C
```

You can also claim an Object in customized Set, but you have to prove the customized Set is a non-empty Set:

```litex
let s set
know $exist_in(s)

have n s
```

`exist_in` is a built-in Exist Proposition, you could use it directly. From the result provided by Litex, `have n s` equals `have n st $exist_in(s)` in Litex.

## Different between `let` and `have`

`let` and `have` looks similar. They can both claim Object. But here is one primary difference is that the Object claimed by `have` is existed by proved but the one claimed by `let` is not.

When you claim an Object by `have`, Litex will check existence of the Object. Now, you know why you must `have` an Object from a non-empty Set.

When you claim an Object by `let`, Litex won't do any check. So, you could claim anything you want by `let`.