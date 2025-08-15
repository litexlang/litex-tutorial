# Know

Many times we need to assume certain facts to be true. For example, we may introduce a new object and assign it specific properties. Or we may want to introduce a fact without proving it. In such cases, we use the `know` keyword.

There are two ways to use `know`: multiple lines and inline.

Multiple line version requires you to write `know` followed by `:`. The facts here can be inline fact or multiple lines fact.

```litex
know:
    fact_1
    fact_2
    ...
```

For example (the facts here are always-true facts just for demonstration)

```litex
know:
    1 > 0
    forall x R:
        x $in R
    forall x R => x $in R
    2 > 1
```

Inline version requires you to write `know` followed by a sequence of inline facts. Specific facts are ended with `,` and universal facts are ended with `;`. The last fact ending signal can be omitted.

```litex
know specific_fact_1, universal_fact_1; specific_fact_2, universal_fact_2; ...
```

```litex
know 1 > 0, forall x R: x $in R; forall x R => x $in R; 2 > 1
```

When you want to declare an object with some properties, you can use `know`

For example, we can define a function `fibonacci` and claim some facts about it.

```litex
fn fibonacci(n N_pos) N_pos
know fibonacci(1) = 1, fibonacci(2) = 1, forall n N_pos: fibonacci(n+2) = fibonacci(n+1) + fibonacci(n)

fibonacci(10)
```

For example, we can declare a positive natural number `n` that is larger than 10.

```litex
let n N_pos
know n > 10
```

It is equivalent to the following code:

```litex
let n N_pos: n > 10
```

You can also claim a proposition and bind properties to it using `know`.

```litex
prop n_larger_than_10(n N_pos) # declare a proposition
know forall n N_pos: n > 10 <=> $n_larger_than_10(n)
```

It is equivalent to the following code:

```litex
prop n_larger_than_10(n N_pos):
	n > 10
```

Sometimes you just want to assume a fact without checking. For example, axioms are always true. You can use `know` to assume them.

For example, 0 is by axiom the smallest natural number.

```litex
know forall x N => x >= 0
```

Sometimes we want to use a fact without proving it. We can just use `know` to assume it. Be careful when you do so! It is very easy to introduce wrong facts.

```litex
prop fermat_last_theorem(x, y, z, n N_pos): n >= 3 <=> x^n + y^n = z^n
know forall x, y, z Z, n N_pos: n >= 3 => $fermat_last_theorem(x, y, z, n)
```