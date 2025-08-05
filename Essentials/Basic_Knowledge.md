# Basic Knowledge

## Number

all numbers like `0`, `3.14159`, `-1` are Number. You could use it directly in Litex.

```litex
1 = 1
```

## Object

In real life, we can call anything an object. Also, in our language, all entities are objects.

Litex use `let` to claim an Object.

```litex
let something obj
```

## Set

Same as the definition in math, a set is collection of different things(Object).

Set itself is also an Object. So you could still use `let` to claim a Set.

```litex
let s set
```

There, you claimed an empty set without any feature. In Litex, there are build-in sets: `R`, `N`, `N_pos`, `Z`.

## Let

To express that an object is in a set, we use `let`, too. You can claim an Object `n` which is in the set `N`.:

```litex
let n N
```

Also, you could claim Objects in one line:

```litex
# claim Objects n, m in N
let n, m N
```

> Note: Above line is same as the line `let n N, m N`. Here is a syntactic sugar for you.

```litex
# claim Objects n, m in N and z in Z
let n, m N, z Z
```

```litex
# claim empty set s and Object n in s
let s set, n s
```

> Note: You can't change the claim order in last example. `s` must be claimed first because `n` cannot be claimed before Litex know what is `s`

## Know

Sometimes, we hope to claim some knowledge is correct by default. We could use `know` to claim it:

```litex
know 1 = 1

know 1 = 2
```

As you can see, `know` is powerful and dangerous. **Use it carefully.**

> Note: Sometimes, you could set some fact as `know` temporarily and try to prove it later. Then, you can continue your workflow more smoothly.
