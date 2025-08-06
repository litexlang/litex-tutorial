# Not

Not means the negation of a statement or [Proposition](https://litexlang.org/doc/Turorial/Proposition). You can use it like:

```litex
let n R:
    n > 5

not n <= 5
```

```litex
prop form_triangles(x, y, z R):
    x > 0
    y > 0
    z > 0
    iff:
        x + y > z
        x + z > y
        y + z > x

not $form_triangles(1, 2, 3)
```