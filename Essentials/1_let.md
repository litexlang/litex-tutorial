# Let

On last chapter, you've learned how to claim an Object or a Set. Here, we would introduce one more usage of `let`.

To express that an object is in a set, we use `let`, too:

```litex
let n N
```

Here, we claimed an Object `n`, which is in the set `N` (the set of natural numbers).

Also, you could claim Objects in one line:

```litex
# claim Objects n, m in N
let n, m N
```

```litex
# claim Objects n, m in N and z in Z
let n, m N, z Z
```

```litex
# claim empty set s and Object n in s
let s set, n s
```

> Note: you can't change the claim order in last example. `s` must be claimed first because `n` cannot be claimed before Litex know what is `s`