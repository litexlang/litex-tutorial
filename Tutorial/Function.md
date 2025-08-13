# Function

Functions are one of the most important concepts in math. They are used to describe the relationship between two quantities. Although Litex is still a computer language, it is very different from programming languages like Python and C, because Litex is very close to math and math is different from programming. You can see such gap by viewing the difference of the concept of `function` in math and programming.

In programming like Python or Lean, a function is a block of executable code that performs computation or side effects. In math, a function is a symbol that builds a new symbol from input symbols (no execution). In both math and programming, you can think of a function as a symbol that uses `()` to wrap its input symbols to form a new symbol. For example, `square_root(x)` is a function that takes an input `x` and returns a new symbol `square_root(x)` without any execution.

## Define a Function

You can define a Function `square_root`(for all `x` in `R`, if `x` >= 0, then there is some special value in `R` make `square_root(x) * square_root(x)` equals `x`):

```litex
fn square_root(x R) R:
    dom:
        x >= 0
    then:
        square_root(x) * square_root(x) = x
```

- `fn` is the reserved word of Function. You can declare a new function by using `fn`.
- `square_root` is the name of this Function. 
- String in parentheses, `x R`, are Object-Set pairs (and the set they're in) which will be used in this Function. e.g. function `square_root` takes an Object `x` in the set `R` as parameter.
- The last word in the first line, `R`, means the *range* (co-domain) of this Function. e.g. the range of `square_root` is `R`. In this case, `forall x R: square_root(x) $in R` is by definition true.
- `dom` is the additional restrictions for those Objects, which is the *domain* of this Function. When you pass objects into a Function, you should make sure the objects are in the domain. For example, `square_root(-1)` is invalid because `-1` is not in the domain of `square_root`: `-1 >= 0` is not true.
- `then` contains facts that the function satisfies. For example, `forall x R: x >= 0 => square_root(x) * square_root(x) = x` is by definition true. Such facts are by definition true, without any proof. So you must be careful when you are defining function properties with `then`. For example, if you mistype `square_root(x) * square_root(x) = -1`, which is absurd, you would not get any error from Litex. 

**NOTE FROM THE AUTHOR: If you want to declare a function with safe guarantee, you should use keyword `set_defined_by_replacement` instead of `fn`. This functionality will be implemented soon. Sorry for the inconvenience.**

Litex encourages you to write clean and short code. For example, you could hide `dom` when you write Function `square_root` like this:

```litex
fn square_root(x R) R:
    x >= 0
    then:
        square_root(x) * square_root(x) = x
```

Litex respects users’ habits, which helps close the gap between them and the language, making them more willing to use Litex in their daily work. When writing mathematics, people are used to putting everything on one line, so Litex also allows users to do the same. There is inline version of fn definition. It is the same as the above definition. Inline version is more compact and aligned to daily writing habits of mathematicians.

```litex
fn square_root(x R) R: x >= 0 => square_root(x) * square_root(x) = x
```

You can define a Function without `then` and `dom`, but only a name like the following line, which means a Function with domain and range but no dependency. For example, `function` defined here is a Function that takes an Object `x` in the set `N` as parameter and returns a value in the set `R`. So `forall x N: function(x) $in N` is by definition true.

```litex
fn function(x N) R
```

Of course, you can define a Function with specified domain with `dom`, which express the similar meaning like the above line.

```litex
fn function(x R) R:
    dom:
        x > 0
```

When there is no `dom`, you can hide both `dom` and `then` like this. For example, `forall x R: f(x) > 0` is by definition true.

```litex
fn function(x R) R:
    f(x) > 0
```

> Note: If there is only `dom` in your Function, you can't hide `dom` anymore. Or Litex would misunderstand your lines with the situation that Function with `then` only.

## Call a Function

Just like the way we use function in math, you can call a function by `functionName(parameters)`. For example, `square_root(4)` is a function call.

```litex
fn square_root(x R) R:
    x >= 0
    then:
        square_root(x) * square_root(x) = x

square_root(4) $in R
```

> Note: Litex is a formal language **to PROVE** instead of to compute, so `square_root(4)` here is not equal 2. `square_root(4)` here means there is a value in `R` that makes `square_root(x) * square_root(x) = x` and we don't care which number is the value.

## Declare Function from Function Template Using `let`

Functions are also objects. Since `let` can be used to declare objects, you can also use it to declare a Function.

```litex
# declare a function template
fn_template finite_sequence(s set, max N):
    fn (n N) R:
        dom:
            n < max

let n N

# declare a function with a function template
let fs1 finite_sequence(R, 10):
    fs1(n) = n * n
```

As you learned on last section, lines here is the shorter style of the following codes.

```litex
fn_template finite_sequence(s set, max N):
    fn (n N) R:
        dom:
            n < max

let fs1 finite_sequence(R, 10):

know forall n N:
    fs1(n) = n * n
```

