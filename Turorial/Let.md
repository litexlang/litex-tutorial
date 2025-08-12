# Let

In mathematics, anything can be considered an *object*. When you want to use an object in Litex, you must first declare it. The most common way to declare an object is with `let`. In Litex, `let` is used to declare an object by giving it a **name** and specifying the **set** it belongs to. 

```litex
let object_name set_it_belongs_to
```

For example, to declare an object `n` in the set `N` (natural numbers):

```litex
let n N
```

You must declare an object before using it, and object names must be unique. For example, when you have already `let a N`, you can not `let a N` again.

You could claim multiple Objects in one line.

```litex
let n N, m N
```

Declaring multiple objects in one line is common because sometimes we want to declare multiple objects with relations between them. For example, you can claim two natural numbers `n` and `m` such that `n > 0` and `m > n`. You can also attach facts to objects at the time of declaration using `:`. For example, the following declares two natural numbers `n` and `m` such that `n > 0` and `m > n`:

```litex
let n, m N:
    n > 0
    m > n
```

As you might guess, 

Notice `let n, m N` is the same as `let n N, m N`. This is a syntactic sugar in Litex: when declaring multiple objects that belong to the same set, you can list their names separated by commas, followed by the set name. Such syntactic sugar also works for statements like `fn`, `forall`, `prop` etc, where the user wants to declare multiple objects with the same set.

You can claim objects with different sets in one line, too. For example, you can claim an Object `n` in `N` and an Object `z` in `Z` in one line:

```litex
let n, m N, z Z
```

You can even claim an Object in a Set which you just claimed.

```litex
let s set, n s
```

> Note: You can't change the claim order in last example. `s` must be claimed first because `n` cannot be claimed before Litex know what is `s`

For Objects with multi-restrictions like claiming multivariate linear equation (2x + 3y = 10, 4x + 5y = 14):

```litex
let x, y R:
    2 * x + 3 * y = 10
    4 * x + 5 * y = 14
```

