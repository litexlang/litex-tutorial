# Function

Same as the definition in math, Function means how a varying quantity depends on another quantity.  

## Define a Function

You can define a Function `square_root`(for all `x` in `R`, if `x` >= 0, then there is some special value in `R` make `square_root(x) * square_root(x)` euqals `x`):

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
- The last word in the first line, `R`, means the *codomain* of this Function.
- `dom` is the additional restrictions for those Objects, which is the *domain* of this Function.
- `then` means the part *then* in a Function. So you should write the dependency after *then* in `then`.

To make definition lines less, you could hide some reserved word for some situation. For example, you could hide `dom` when you write Proposition `square_root`:

```litex
fn square_root(x R) R:
    x >= 0
    then:
        square_root(x) * square_root(x) = x
```

If you claim `x` in `N` in the first line, there is no `dom` anymore. Then, you could hide `then`. Function `square_root` could also be writen like:

```litex
fn square_root(x N) R:
    square_root(x) * square_root(x) = x
```

For this definition, codomain of Function is still `R`, but domain of Function is `N` because there is no `dom`.

Just like the feature of Proposition, you can define a Function without `then` but only a name like the following line, which means a Function with domain and codomain but no dependency:

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