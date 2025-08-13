# A Simple Example

_If you define the problem correctly, you almost have the solution._

_-- Steve Jobs_

Mathematics is the art of deriving new facts from established ones. To illustrate, consider a classical syllogism proposed by Aristotle, which formalizes deductive reasoning as follows. Run this example on [playground](https://litexlang.org/playground):

This example means: All humans are intelligent. Jordan is a human. Therefore, Jordan is intelligent. It is a very typical syllogism example. (本例是一个典型的三段论例子：所有人类都是聪明的。乔丹是人类。因此，乔丹是聪明的。)

<table style="border-collapse: collapse; width: 100%; font-size: 12px">
  <tr>
    <th style="border: 2px solid black; padding: 4px; text-align: left; width: 40%;">Litex</th>
    <th style="border: 2px solid black; padding: 4px; text-align: left; width: 60%;">Lean 4</th>
  </tr>
  <tr>
    <td style="border: 2px solid black; padding: 2px; line-height: 1.5">
      <code>let human set, Jordan human</code> <br><br>
      <code>prop intelligent(x Human)</code> <br><br>      <code>know forall x Human:</code> <br>
      <code>&nbsp;&nbsp;$intelligent(x)</code> <br> <br>
      <code>$intelligent(Jordan)</code>
    </td>
    <td style="border: 2px solid black; padding: 2px; line-height: 1.5">
      <code>def Human := Type</code> <br><br>
      <code>def intelligent (x : Human) : Prop := true</code> <br><br>
      <code>axiom intelligent_all :</code><br>
      <code>&nbsp;&nbsp;∀ (x : Human), intelligent x</code> <br><br>
      <code>example (Jordan : Human) : intelligent Jordan := intelligent_all Jordan</code>
    </td>
  </tr>
</table>

The above example means: `Human` is the set of all humans. Using `know`, we establish a simple fact: all humans are intelligent. When the user input `intelligent(Jordan)`, the system will automatically find the fact `forall x Human: $intelligent(x)` and substitute `x` with `Jordan`, and then check if the result is true. This process is called `match and substitution`. Since Jordan is in the set of `Human`, "Jordan is intelligent" is true.

Each statement in Litex has four potential outcomes: true, false, unknown, or error. Factual statements start with `$` to differentiate them from functions.[^1]

When you run the above example on [playground](https://litexlang.org/playground), you might see the output similar to this:

```
Jordan = Jordan
is true. proved by
literally the same
human = human
is true. proved by
literally the same
$in(Jordan, human)
is true. proved by
$in(Jordan, human)
Jordan matches Jordan
human matches human

$intelligent(Jordan)
is true. proved by
forall x human:
    $intelligent(x)
```

It says how the factual statement `$intelligent(Jordan)` is verified by the Litex kernel based on the established facts. Here a universal fact `forall x Human: $intelligent(x)` is used to verify the specific factual statement `$intelligent(Jordan)`. Keep this example in mind. This is the most classic example of how people uses `match and substitution` to establish new facts. Refer to this example when you are reading the next section. The kernel prints out how it verifies the statement, so you can see how it works.

[^1]: Factual expressions are typically written as `$propName(objects)`. They begin with `$` to differentiate them from functions. Litex is a language close to everyday math, that is why it provides 3 handy exceptions to make your code nicer: 1. builtin keywords like =, > are written as daily life math 2. If the proposition requires one and only one object, it can be written as `object $propName` 3. If the proposition requires two objects, it can be written as `object1 $propName object2`.

