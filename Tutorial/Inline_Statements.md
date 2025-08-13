# Inline Statements

People are always more receptive to things they’re familiar with. That’s why Litex adopts Python-style syntax, using line breaks to structure code. This not only keeps the code organized but also lowers the learning curve for users.

However, in daily writing, people are accustomed to writing statements in a single paragraph. Using Python-style syntax can sometimes make code occupy excessively many lines. So Litex provides a way to write statements in a single line.

## Forall

Inline forall statement ends with `;` to separate itself from the next statement. When the whole line ends with that forall statement, the `;` is optional. When `forall` is inside another statement, the `;` is required.

```litex
forall => 1 + 1 = 2
forall : 1 > 0 => 1 > 0
forall => 1 + 1 = 2 <=> 1 + 1 = 2
forall x R => x $in R
forall x R => x > 0 <=> x > 0
forall x R: x > 0 => x > 0 <=> x > 0
forall x R: forall y R: y > 0 => y > 0 <=> y > 0; x > 0 => x > 0
forall x R: forall y R: y > 0 => y > 0 <=> y > 0; x > 0 => forall y R: y > 0 => y > 0 <=> x > 0
forall x R: forall x R: x > 0 => x > 0; 1 > 0, forall x R: x > 0 => x > 0; => 1 > 0, forall x R: x > 0 => x > 0; 1 > 0
```

```litex
forall:
    1 + 1 = 2

forall:
    1 > 0
    then:
        1 > 0

forall:
    then:
        1 + 1 = 2
    iff:
        1 + 1 = 2

forall x R:
    x $in R

forall x R:
    then:
        x > 0
    iff:
        x > 0

forall x R:
    forall y R:
        dom:
            x > 0
        then:
            x > 0
        iff:
            x > 0
    x > 0
    then:
        x > 0

forall x R:
    forall y R:
        dom:
            y > 0
        then:
            y > 0
        iff:
            y > 0
    x > 0
    then:
        forall y R:
            dom:
                y> 0
            then:
                y > 0
            iff:
                y > 0
```

## Function Declaration

``` litex
fn f(x R) R: x > 0 => f(x) > 0
fn h(x N) N: forall y N_pos: x < y
fn g(x R) R => g(x) > 0
fn k(x N) N: forall y N_pos: x < y => f(x) = 0
```

```litex
fn f(x R) R:
    x > 0
    then:
        f(x) > 0

fn h(x N) N:
    dom:
        forall y N_pos:
            x < y

fn g(x R) R:
    g(x) > 0

fn k(x N) N:
    forall y N_pos:
        x < y
    then:
        f(x) = 0
```

## Proposition Declaration

The followings are inline version of proposition declaration. The equivalent multiple lines version is below.

```litex
prop q(x R) <=> x > 0
prop p(x , y R): x > 0, y > 0 <=> x + y > 0
```

```litex
prop q(x R):
    x > 0

prop p(x , y R):
    x > 0
    y > 0
    iff:
        x + y > 0
```

## Inline Multiple Factual Statements



## Claim
