# Factual Statement

_Mathematics is nothing more than a game played according to certain simple rules with meaningless marks on a paper._

_-- David Hilbert_

## What is a Factual Statement?

The most fundamental concept in both mathematics and Litex is the Factual Statement.

A Factual Statement is a statement whose truth value can be one of the following:

true

false

unknown (not enough information to prove or disprove it)

error (e.g., syntax error)

Do not confuse a Factual Statement with a true statement—a Factual Statement may be false, unknown, or error.
Also, do not confuse a Factual Statement with a Proposition. A Proposition is like a “verb” waiting for objects to be supplied; once those objects are provided, it becomes a Factual Statement.

## Deriving new facts from established ones by `match and substitution`

Math is about deriving new facts from established ones. Verification is about making sure the new facts are true based on the established ones. There are and only are two ways of verifying a new fact:

1. From special case to special case. e.g. `a = 1` => `a = 1`. The derived fact `a = 1` (the second statement) is true because the first statement is true and the first statement is written exactly the same as the second statement. I call it `match`.

2. From general case to special case. e.g. `forall x Human: $intelligent(x)` => `$intelligent(Jordan)`. The derived fact `intelligent(Jordan)` is true because by substituting `x` with `Jordan`, the first statement is true, and the second statement is written exactly the same as the first statement after substitution. I call it `match and substitution`.

`General Fact` and `Specific Fact` are two types of factual statements. Everything in Litex happens around these two types of factual statements.

You just learned how Litex builds math from basic pieces, like building blocks. To sum up, `match and substitution` is the basic way of deriving new facts from established ones. We can construct the whole math system by this way in Lite as long as basic arithmetic and counting are built-in. [^3][^4][^5][^6][^7]

## How to call a Factual Statement?

The basic process of deriving a new fact from established ones is by writing factual statements one after another. Verification of every factual statement is done automatically by Litex kernel using `match and substitution`. But we should declare a proposition first. We declare a proposition like this:

```litex
prop large_than_zero(x R):
    x > 0
```

Then we can use it to prove something like this:

```litex
$large_than_zero(1)
```

As you can see, `large_than_zero` is a proposition. `>` is a built-in proposition. When we put `1` into `large_than_zero`, it becomes a Factual Statement `$large_than_zero(1)`. In this case, since `1 > 0` is true, `$large_than_zero(1)` is true. We use symbol `$` to distinguish a Factual Statement from a function.

When a proposition takes exactly two objects, you can write the proposition name infix. Litex allows you to do so because that Litex wants the user to feel as if they are writing daily math and have familiar feelings.

```litex
$in(1, N)
1 $in N
```

<!-- TODO: 说明有哪些 builtin 的 proposition. -->

[^3]: There are exceptions. Facts about symbols with literal information (e.g. numbers like 1, 2, 3, counting etc) are not verified in this way. Facts related to counting are not verified in this way. There are and only these two exceptions. Those facts are verified by Litex's builtin rules, the user does not need to worry about them.

[^4]: Voltaire once said: "Common sense is not so common." In the case of Litex, Litex makes the process of building math as easy as `ctrl+f & ctrl+r /cmd+f & cmd+r` in your browser, by discovering that math is nothing but a special kind of `match and substitution` problem. Everyone is so familiar with this process, but almost no one actually finds its significance and use this idea to create a simple formal language. The real magic of Litex is that it works just like how people think in daily life. This is a hard magic for the language designer, because it requires a deep understanding of both the nature of mathematics and the nature of programming, but is worth the effort.

[^5]: In naive set theory, where almost all daily math is based on, all facts are derived by `match and substitution` using first-order logic, with only two exceptions: 1. mathematical induction. 2. the axiom of replacement. Those two are builtin in Litex. Since high-order logic is "passing proposition as parameter to another proposition", facts about high-order logic are still verified by `match and substitution`. Litex will implement high-order logic in the future. If you are still worried about whether Litex is rigorous, the Litex kernel prints out how it verifies the statement, so you can see how it works.

[^6]: Litex is a very simple language to learn. In fact, I am not sure whether I should use "learn" to describe it. Most of Litex language features are so common sense that we use it everyday to reason. I guess people can not "learn" what they have already known! A lot of people may think math is hard, but what Litex does is to make math as easy as `ctrl+f & ctrl+r /cmd+f & cmd+r` in your browser. Let more people find pleasure in the wonderful world of math!

[^7]: Carful readers may worry the foundation of Litex is shaky, because `match and substitution` is not a very rigorous concept. They might think Type theory, where Lean is based on, is more solid. I disagree. First, the kernel of type system in Lean is just a huge piece of C++ code, doing `match and substitution`. Second, no matter what mathematical foundation a traditional formal language is based on (in the case of Lean, it is Type theory), it is still a programming language, which is no different from Python. The syntax style of Lean makes it sort of easier to write formal proofs, but it is still very very far from what we are truly thinking when we are doing math, because the semantics of Lean is still a programming language. All language designers agree it is the semantic that matters more, not the syntax. Litex has a semantics designed to be as close to the way we think in daily life as possible.
