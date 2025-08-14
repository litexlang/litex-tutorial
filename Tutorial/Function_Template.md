# Function Template

Sometimes we want to define a set of functions with certain properties. For example, we want to define the set of all finite positive sequences (a sequence is a function from natural numbers to some set) with at least 10 items. We can do this by defining a function template.

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

Function template can be very helpful, especially when we are defining multiple functions with similar structure.

Function Template is a Litex tool to help users define Function more easily. Also, you could regard it as a set of Functions.

## Define a Function Template

The way defining Function Template looks like how we define a Function. You can define a `finite_sequence` (a sequence with):

```litex
fn_template finite_sequence(s set, length N):
    fn (n N) R:
        dom:
            n < length
```

<!-- TODO 定义fn_template的时候是不是没法提供then，因为fn目前匿名，需要在let fn的时候填写then -->

## Define a Function via Function Template

Litex provides Function Template to help users get rid of the quagmire of rewriting method definitions.

Sometimes, we have to define some similar Functions. For example, in some situation, you have to define some finite sequences with different length. Without Function Template, the Litex code would be:

```litex
fn fs1(n N) R:
    n < 10
    then:
        fs1(n) = n

fn fs2(n N) R:
    n < 20
    then:
        fs1(n) = n * n

fn fs3(n N) R:
    n < 30
    then:
        fs1(n) = n * n * n
```

As you can see, most lines are similar. You are repeating a boring work. With Fucntion Template, lines goes like:

```litex
fn_template finite_sequence(s set, length N):
    fn (n N) R:
        dom:
            n < length

let n N:

let fs1 finite_sequence(R, 10):
    fs1(n) = n

let fs2 finite_sequence(R, 20):
    fs2(n) = n * n

let fs3 finite_sequence(R, 30):
    fs3(n) = n * n * n
```

Looks much pretty, huh?