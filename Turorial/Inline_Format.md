# Inline Format

To align to the writing habits of mathematicians. Litex provides Inline Format.

| Symbol | usage                                   |
| :----- | :-------------------------------------- |
| `:`    | `:` is equal to every `dom` in Litex.   |
| `=>`   | `=>` is equal to every `then` in Litex. |
| `<=>`  | `<=>` is equal to every `iff` in Litex. |
| `or()` | `or()` is the Inline Format of `or`.    |

For the last example in chapter [Forall](https://litexlang.org/doc/Turorial/Forall), it could be replaced by:

```litex
forall x R: x > 1 => x <= 2 <=> not x > 2
```

For the first example in chapter [Proposition](https://litexlang.org/doc/Turorial/Proposition), it could be replaced by:

```litex
prop form_triangles(x, y, z R): x > 0, y > 0, z > 0 <=> x + y > z, x + z > y, y + z > x
```

For the example in chapter [Or](https://litexlang.org/doc/Turorial/Or), it could be replaced by:

```litex
let x R: x = 1
or(x = 1, x = 2)
```