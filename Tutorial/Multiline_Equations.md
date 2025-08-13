# Multiline Equation

Litex provides `=:` to express a multiline equation:

```litex
let x, y R:
    x = -4
    y = 6
=:
    2 * x + 3 * y
    2 * -4 + 3 * 6
    10
=:
    4 * x + 5 * y
    4 * -4 + 5 * 6
    14
```