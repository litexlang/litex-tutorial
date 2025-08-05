# Function Template

Function Template is a Litex tool to help users define Function more easily. Also, you could regard it as a set of Functions.

## Define a Function Template

The way defining Function Template looks like how we define a Function. You can define a `seqence`():

```litex
fn_template seqence(x R):
    dom:
        x >= 0
    fn (y N) R:
        dom:
            y >= 0
        then:
            square_root(x) * square_root(x) = x
```

- `fn_template` is the reserved word of Function Template
- `seqence` is the name of Function Template
- String in parentheses, `x R`, are Objects (and the set they're in) which will be used in this Function Template.
- `fn` part is just like the rule of the definition of Function without Function name.
- all the features from defining a Function fit Function Template such as hiding `dom`, hiding `then` and etc. 

## Define a Function via Function Template

Litex provides Function Template to help users get rid of the quagmire of rewriting method definitions.

Sometimes, we have to define some similar Functions. For example, in some situation, we hope to devide square root by positive and negtive. Without Function Template, the Litex code would be:

```litex
fn positive_square_root(x R) R:
    dom:
        x >= 0
    then:
        square_root(x) * square_root(x) = x
        square_root(x) > 0

fn negtive_square_root(x R) R:
    dom:
        x >= 0
    then:
        square_root(x) * square_root(x) = x
        square_root(x) < 0
```

As you can see, 66% of code of them are duplicated. With Fucntion Template, code goes like:

```litex
fn_template square_root(x R) R:
    dom:
        x >= 0
    then:
        square_root(x) * square_root(x) = x

let positive_square_root square_root:
    positive_square_root(x) > 0

let negtive_square_root square_root:
    negtive_square_root(x) < 0
```