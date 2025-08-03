# Know

Sometimes, we hope to claim some knowledge is correct by default. We could use `know` to claim it.

On Proposition chapter, we claimed a empty Proposition `form_triangles`, which is obviously false. But here we could claim it true by `know`:

```litex
prop form_triangles(x, y, z R)

know:
    forall n, m, l R:
        $form_triangles(n, m, l)

$form_triangles(1, 2, 3)
```

As you can see, `know` is powerful and dangerous. It is always used with `forall` together to express that you consider this Proposition is true in *this speical situation*.

> Note: Sometimes, you could set some fact as `know` temporarily and try to prove it later. Then, you can continue your workflow more smoothly.