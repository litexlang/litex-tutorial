# Factual Statement

The most fundamental concept in both mathematics and Litex is the Factual Statement.
A Factual Statement is a statement whose truth value can be one of the following:

true

false

unknown (not enough information to prove or disprove it)

error (e.g., syntax error)

Do not confuse a Factual Statement with a true statement—a Factual Statement may be false, unknown, or error.
Also, do not confuse a Factual Statement with a Proposition. A Proposition is like a “verb” waiting for objects to be supplied; once those objects are provided, it becomes a Factual Statement.

We declare a proposition like this:

```litex
prop large_than_zero(x R):
    x > 0
```

Then we can use it to prove something like this:

```litex
$large_than_zero(1)
```

As you can see, `large_than_zero` is a proposition. `>` is a built-in proposition. When we put `1` into `large_than_zero`, it becomes a Factual Statement `$large_than_zero(1)`. In this case, since `1 > 0` is true, `$large_than_zero(1)` is true. We use symbol `$` to distinguish a Factual Statement from a function.
