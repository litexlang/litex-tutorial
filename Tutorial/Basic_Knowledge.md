# Basic Knowledge

## Number

all numbers like `0`, `3.14159`, `-1` are Number. You could use it directly in Litex.

```litex
1 = 1
```

## Object

Anything in math can be called an object. Litex use `let` to claim an Object. When we declare an object, we should give it a name and the set it belongs to. i.e.

```litex
let object_name the_set_it_belongs_to
```

For example, you can claim an Object `n` which is in the set `N` (natural number):

```litex
let n N
```

Only after you declare something can you use it and you can not duplicate the name of an object. When using `let` to declare an object, you can also bind some facts to it using `:`. For example, you can claim an Object `n` which is in the set `N` and larger than 0 and also declare an object `m` which is larger than `n`:

```litex
let n N, m N:
    n > 0
    m > n
```

## Set

Same as the definition in math, a set is collection of different things(Object). Modern math is based on Set Theory. Since Litex is designed as close to modern math as possible, it is also based on Set Theory. When you declare an object, you should also declare the set it belongs to. Specifying the set is important because it tells both humans and the system what kind of object you are talking about. It makes your statements precise and allows the system to check whether your operations and reasoning steps are valid. It also enables automatic discovery of errors, e.g., trying to add a number to a function, or applying a theorem to the wrong kind of object.

Set itself is also an Object. So you could still use `let` to claim a Set.
```litex
let s set
```

There, you claimed an empty set without any feature. In Litex, there are build-in sets: `R`, `N`, `N_pos`, `Z`.

## Know

Sometimes, we hope to claim some knowledge is correct by default. It can be a fact that is so obvious that we don't need to prove it, or can be the basic assumption of the proof, or can be an axiom. We could use `know` to claim it. For example, you can claim that `n` is larger than 0 by default:

```litex
let n N

know n > 0
```

`know` can be very helpful when you want to focus on the main logic of your proof and not be bothered by the details. You can use `know` to make it true and come back to prove it later. However, `know` is powerful and dangerous. For example, you can claim that `1` is equal to `2` by default, which is obviously wrong:


```litex
know 1 = 2
```

Use `know` carefully.





