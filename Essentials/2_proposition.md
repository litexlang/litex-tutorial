# Proposition

## Claim a Proposition

You can claim a Proposition `form_triangles`(`x`, `y`, `z` in `R` is able to form triangles if and only if the sum of any two is greater than the third one):

```litex
prop form_triangles(x, y, z R):
    dom:
        x > 0
        y > 0
        z > 0
    iff:
        x + y > z
        x + z > y
        y + z > x
```

`prop` is the reserved word of Proposition. `form_triangles` is the name of this Proposition. String in parentheses are Objects (and the set they're in) which will be used in this Proposition. `dom` is the additional restrictions for those Objects. `iff` means the part *if and only if* in a Proposition. So you should write the logic after *if and only if* in `iff`.

To make claim lines less, you could hide some reserved word for some situation. For example, you could hide `dom` when you write Proposition `form_triangles`:

```litex
prop form_triangles(x, y, z R):
    x > 0
    y > 0
    z > 0
    iff:
        x + y > z
        x + z > y
        y + z > x
```

If you claim `x`, `y`, `z` in `N_pos` (the set of positive natural numbers) in the first line, there is no `dom` anymore. Then, you could hide `iff`. Proposition `form_triangles` could also be writen like:

```litex
prop form_triangles(x, y, z N_pos):
    x + y > z
    x + z > y
    y + z > x
```

## Call a Proposition

After claiming a Proposition, you could call it anywhere with a prepend `$`:

```litex
prop form_triangles(x, y, z R):
    x > 0
    y > 0
    z > 0
    iff:
        x + y > z
        x + z > y
        y + z > x

$form_triangles(3, 4, 5)
```

If there is only two Objects in parentheses of Proposition claim, you could also call it like:

```litex
prop divisible_by(n, m R):
    m != 0
    iff:
        n % m = 0

6 $divisible_by 3
```