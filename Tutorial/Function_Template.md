# Function Template

Sometimes we want to define a set of functions with certain properties. For example, we want to define the set of all finite positive sequences (a sequence is a function from natural numbers to some set) with at least 10 items. We can do this by defining a function template.

Function template can be very helpful, especially when we are defining multiple functions with similar structure.

A function template in Litex looks like this:

```
fn_template T(template-parameter-parameter-set-pairs):
    template_dom_fact_1
    ...
    fn (function-parameter-parameter-set-pairs) the_set_where_the_return_value_of_this_function_belongs_to:
        dom_fact_1
        dom_fact_2
        ...
        =>:
            then_fact_1
            then_fact_2
            ...
```

You might be wondering, what does a function in a function template actually means. For example, what does `f $in T(parameters)` mean? It means:

1. The domain of f is superset of the domain of the `fn` under declaration of T: the domain of `f` satisfies function-parameter-parameter-set-pairs, and dom_fact_1, dom_fact_2, ...

2. When restricted on the domain of the `fn` under declaration of T, the function f satisfies all the then facts in `fn`: `f` satisfies `then_fact_1`, `then_fact_2`, ... and the return value is in set `the_set_where_the_return_value_of_this_function_belongs_to`

For example, we define the set of all finite positive sequences with at least 10 items. 

```litex
fn_template finite_positive_sequence_with_at_least_10_items(length N_pos):
    length >= 10
    fn (n N_pos) R:
        n <= length
        then:
            finite_positive_sequence(n) > 0

let f finite_positive_sequence_with_at_least_10_items(12)
```

The `f` here is equivalent to `f` defined here.

```litex
fn f(n N_pos) R:
    n <= 12
    then:
        f(n) > 0
```

When there is no further template parameter requirements, you can hide the template parameter set pairs. For example:

