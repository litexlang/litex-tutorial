# Proposition

Same as the definition in math, Proposition is a sentence that is either true or false, but not both.

## Claim a Proposition

You can claim a Proposition `form_triangles`(`x`, `y`, `z` in `R` and `x > 0`, `y > 0`, `z > 0` is able to form triangles if and only if the sum of any two is greater than the third one):

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

`prop` is the reserved word of Proposition. `dom` is the additional restrictions for those Objects. `iff` means the part *if and only if* in a Proposition. So you should write the logic after *if and only if* in `iff`.

Just like you add additional restriction on `forall`, you use `dom`! And as it should be, `dom` here could be hidden here as well:

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

You should have thought of it as well, If you claim `x`, `y`, `z` in `N_pos`, you could hide the `then` because there is no `dom`:

```litex
prop form_triangles(x, y, z N_pos):
    x + y > z
    x + z > y
    y + z > x
```

## Claim an empty Proposition

Also, you can claim a Proposition without any logic but only a name like the following line, which means `x`, `y`, `z` in `N_pos` is able to form triangles in any situation. Obviously, this proposition is false with the knowledge we have. But you can still claim it anyway.

```litex
prop form_triangles(x, y, z N_pos)
```

Absolutly, you can claim a Proposition with only additional restrictions and no logic like the following lines, which express the similar meaning like the above line:

```litex
prop form_triangles(x, y, z R):
    dom:
        x > 0
        y > 0
        z > 0
```

> Note: If there is only dom in your Proposition, you can't hide `dom` anymore. Or Litex would misunderstand your lines with the situation that Proposition with `iff` only.

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

## Make a Proposition always True

Litex could judge if a Propsition is true of false when user call it. But for the empty Propostion, there is no logic for Litex to judge. You have to make it always true via `know`. Just now, we claimed an empty Proposition `form_triangles`. Litex consider it unknown because we don't give it *if and only if* part:

```litex
prop form_triangles(x, y, z N_pos)

$form_triangles(1, 2, 3)
```

Sometimes, you may want to continue your logic without a specific claim to a Proposition, you can make Litex to consider an empty Proposition true temporarily:

```litex
prop form_triangles(x, y, z N_pos)

know forall m, n, l N_pos:
    $form_triangles(m, n, l)

$form_triangles(1, 2, 3)
```

> Note: Remember to fill the Proposition later. Or your logic looks specious.

## Call Proposition in Restriction

You can call Proposition everywhere you want after claiming. You can call it in restriction:

```litex
prop p(x , y R):
    x < y
    y < 0

know forall x, y R:
    $p(x , y)
    then:
        x < 0

let a, b R
$p(a, b)
a < 0
```

In this case, Litex provides a short style for you to write via `@`:

```litex
@p(x, y R):
    x < y
    y < 0
    then:
        x < 0

let a, b R
$p(a, b)
a < 0
```