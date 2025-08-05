# Let

To express that an object is in a set, we use `let`, too. You can claim an Object `n` which is in the set `N`.:

```litex
let n N
```

## Claim Objects

You could claim Objects `n`, `m` in `N` in one line:

```litex
let n, m N
```

> Note: Above line is same as the line `let n N, m N`. Here is a syntactic sugar for you.

You can claim Objects `n`, `m` in `N` and `z` in `Z` in one line, too:

```litex
let n, m N, z Z
```

You can even claim Object in a Set which you just claimed:

```litex
let s set, n s
```

> Note: You can't change the claim order in last example. `s` must be claimed first because `n` cannot be claimed before Litex know what is `s`

## Claim Objects with additional restriction

If you want to claim an Object with additional restriction, `n` in `N` and `n > 5`, you may write the following lines:

```litex
let n N

know:
    n > 5
```

Above lines work, but Litex provides a shorter style:

```litex
let n N:
    n > 5
```

For Objects with multi-restrictions like claiming multivariate linear equation (2x + 3y = 10, 4x + 5y = 14):

```litex
let x, y R:
    2 * x + 3 * y = 10
    4 * x + 5 * y = 14
```

## Claim Function from Function Template

You can claim [Function](https://litexlang.org/doc/Turorial/Function) from [Function Template](https://litexlang.org/doc/Turorial/Function_Template) via `let`, too:

```litex
fn_template finite_seqence(s set, max N):
    fn (n N) R:
        dom:
            n < max

let fs1 finite_seqence(R, 10):
    fs1(n) = n * n
```