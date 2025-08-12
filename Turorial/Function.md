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

- `fn` is the reserved word of Function. 
- `square_root` is the name of this Function. 
- String in parentheses, `x R`, are Objects (and the set they're in) which will be used in this Function. 
- The last word in the first line, `R`, means the *range* (co-domain) of this Function.
- `dom` is the additional restrictions for those Objects, which is the *domain* of this Function.
- `then` means the part *then* in a Function. So you should write the dependency after *then* in `then`.

To make definition lines less, you could hide some reserved word for some situation. For example, you could hide `dom` when you write Proposition `square_root`:

```litex
fn square_root(x R) R:
    x >= 0
    then:
        square_root(x) * square_root(x) = x
```

There is inline version of fn definition. It is the same as the above definition. Inline version is more compact and aligned to daily writing habits of mathematicians.

```litex
fn square_root(x R) R: x >= 0 => square_root(x) * square_root(x) = x
```

Just like the feature of Proposition, you can define a Function without `then` but only a name like the following line, which means a Function with domain and range but no dependency:

```litex
fn function(x N) R
```

Of course, you can define a Function with only additional restrictions like the following lines, which express the similar meaning like the above line:

```litex
fn function(x R) R:
    dom:
        x > 0
```

> Note: If there is only dom in your Function, you can't hide `dom` anymore. Or Litex would misunderstand your lines with the situation that Function with `then` only.

## Call a Function

Not like the way we call a Proposition, you could call Function anywhere directly after defining a Function:

```litex
fn square_root(x R) R:
    x >= 0
    then:
        square_root(x) * square_root(x) = x

square_root(4) $in R
```

> Note: Litex is a formal language **to PROVE** instead of to compute, so `square_root(4)` here is not equal 2. `square_root(4)` here means there is a value in `R` that makes `square_root(x) * square_root(x) = x` and we don't care which number is the value.

## Declare Function from Function Template Using `let`

Functions are also objects. Since `let` can be used to declare objects, you can also use it to declare a Function. You can claim [Function](https://litexlang.org/doc/Turorial/Function) from [Function Template](https://litexlang.org/doc/Turorial/Function_Template) via `let`, too:

```litex
# declare a function template
fn_template finite_seqence(s set, max N):
    fn (n N) R:
        dom:
            n < max

let n N

# declare a function with a function template
let fs1 finite_seqence(R, 10):
    fs1(n) = n * n
```

As you learned on last section, lines here is the shorter style of the following codes.

```litex
fn_template finite_seqence(s set, max N):
    fn (n N) R:
        dom:
            n < max

let fs1 finite_seqence(R, 10):

know forall n N:
    fs1(n) = n * n
```

