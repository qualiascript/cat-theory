# Fixed Points

We have briefly introduced the concept of a fixed point over an endofunctor `F`, as a point `c` so that `F c = c`.
This is similar to the concept of a fixed point of a function `f`, which is a value `x` so that `f x = x`. Note
that any fixed point must be part of both the domain and the codomain. Then for any `f` we can construct `f'` so that
its domains and codomains are equal and `f'` has the same fixed points as `f`. This shows that it is natural to define
fixed points in terms of an endomorphism.

We have that for any `X :: C`, its inhabitants `x :: X` are isomorphic
to the set of morphisms `f : 1 -> X`. Then the definition of a fixed point becomes: an endomorphism `e : X -> X`
has `x : 1 -> X` as its fixed point if and only if `x . e = x`. As we've previously seen, fixed points encode
a sort of recursive structure, as repeated composition with `e` will not change the result, so if `e` has some
embedding action, we get an infinite embedding.

We have seen that simply typed lambda calculus does not inherently have recursion. Recursive functions call
themselves inside their function body, so we have that `F = G . F`. If we were building up recursion iteratively,
we would have that `F n = G . F (n - 1)`, along with a base case `F 0 = x`, where `n :: FinSet`. Alternatively, we
could write it as `(F n) (F n - 1) = G . (F n - 1)`, or just `F (n, F) = G . (F (n - 1))`. In order to construct up,
we need to start with a skeleton of `F (F', n) = G . (F' (n - 1))` and apply `F` with the second argument as itself.

Let us abstract away the `n` for now. We have a functor `F F'` and we must obtain `F F`, so we need some `Y` so that
`(F F') . Y = F F`. Since this applies for any `F'`, we get that `(F F) . Y = F F`. In other words, `F F` is a fixed
point of the morphism `Y`. As such, in order to have recursion, we must have some morphism `Y` which, when applied
returns a fixed point of `Y`. Then, `Y` is referred to as a fixed point combinator.

## Untyped lambda calculus

We have previously explored simply typed lambda calculus. An alternative model is known as untyped lambda calculus,
which has the property that any function composition with any arguments yields a value. It is defined as such:
given the category of lambda terms `L :: Cat`, not concerning with what the morphisms entail, we have a subcategory
of variables `V :: Set`. Then, for all `x :: V` there is a lambda function `\x. t`, where `t` is any `t :: L`.
Furthermore, for any two terms `t, s :: L`, there is a term `(t s)` called an application.

Since any term `t :: L` can take any other term `s :: L` and return a term, this suggests that each term can be
seen as a functor, and as such we have a functor `app : L -> L ^ L`. A functor `l : L ^ L` is a formulaic method
for mapping each term to another term. Let us assert that each such functor corresponds to some `\x. t`, as untyped
lambda calculus is Turing complete. Then we have a functor `lam : L ^ L -> id L`. We also have that converting
a functor to a lambda function and back yields the same functor, so `lam . app = id(L^L)`.

Then, we have that for any `f :: L ^ L`, there is some `l :: L` so that `lam l = f`. This property is known as
point surjectivity. The terminology of point both in this instance and for fixed points reflects seeing each object
as a featureless point inside the space of the category. More specifically, a point surjective map is any morphism
`m : A -> B` so that every `b : 1 -> B` has a corresponding `a : 1 -> A` so that `a . m = b`.

## Finding fixed points

Does untyped lambda calculus have fixed points? Let us explore this question in more general terms:
`L :: Cat`, but the following apply for any CCC, let us denote it `C : CCC`. We have two objects, `A, B :: C`
and a morphism `m : A -> B ^ A` so that `m` is point surjective. In the case of our untyped lambda calculus model,
we have that `A = B = L`, but this is not generally the case.

Given any `x : B -> B`, we would like to find a `z : 1 -> B` so that `z . x = x`. In fact, this can be constructed
by creating the following morphism: `Q : A -> B`, and for any `a :: A`, `Q a = a . Diag_2 . (m * id) . eval . x`.
We are denoting `(m * id)` the morphism which given a product `a * a`, applies `m` on the left and `id a` on the right.
This exists due to the universal property of products. By expanding, we get `Q a = eval(c . m, c) . x` Since
`Q :: B ^ A`, it can also be denoted as `Q : 1 -> B ^ A`.

Since `m` is a point surjective map, there is some `p : 1 -> A` so that `p . m = Q`. Let us denote `z = Q p : A -> B`.
Then we have `z = eval(p . m, p) . x = eval(Q, p) . x = z . x`. Hence, `z : 1 -> B` is a fixed point of `x : B -> B`.
Thus, we  have the following result, known as the Lawvere Fixed Point Theorem: in any CCC, if there is a point
surjective map `m : A -> B ^ A`, then every `f : B -> B` has fixed points.

## Fixed Point Combinator

This demonstrates that every function in untyped lambda calculus always has a fixed point. In fact, using the proof
as inspiration, we can explicitly construct a fixed point combinator. We have for any `t :: L` a morphism `Q : L -> L`,
`Q l = l . Diag_2 . (app * id) . eval . t`, and a `q :: L` so that `q . app = Q`, and `Q q` is a fixed point of `x`.
Then we need a lambda function `Y :: L` so that `Y x = Q_x q_x`. 

Starting with `Q l = l`, we have `\x. x`. Diagonalization induces `\x. x x`. The first term gets made into a function,
so that we have `\x. \y. x x`, which then gets evaluated back to `\x. x x`. We then apply our morphism `t` to obtain
`\x. t x x`. Then, `Y = Q q` is the result of `(\x. t x x) (\x. t x x) = t (\x. t x x) (\x. t x x)`. In other words,
`Y = t Y`, which is what we wanted. Then let us define the fixed point combinator as `Y = \t. (\x. t x x) (\x. t x x)`.
This construction, also known as the Y-combinator, finds the fixed point of any lambda function.

## Other applications

The Lawvere Fixed Point Theorem says that if there is a point surjective map `m : A -> B ^ A`, then all endomorphisms
of `B` has a fixed point. The contrapositive version implies that if there is an endomorphism `b : B -> B` with no
fixed points, then there is no point surjective map. Let us select `A :: Set`, `B = 2`. There is a function
`f : 2 -> 2`, `f x = 1 - x`, which has no fixed points. As such, there is no surjection `m : B -> 2 ^ B`,
meaning `2 ^ B` has a strictly higher cardinality than `B`. This is known as Cantor's Theorem.

Setting `B` to be the set of natural numbers, this implies that there are more real numbers than natural numbers.
In this regard, the Lawvere Fixed Point Theorem categorifies diagonal arguments. This can be seen by considering one
of the steps in any diagonal argument based proof is the mapping of the diagonal elements so that each element
has a different value from the original one. This requires a function without fixed points.

In fact, the theorem also implies other Gödel's first incompleteness theorem, that the Halting problem is undecidable,
as well as many others seemingly paradoxical results in mathematics such as Russell's Paradox. These results are
connected by explicitly or implicitly using a diagonal argument. Philosophically, it shows that any mathematical
system that is complex enough to talk about itself must either have badly-behaved fixed points, or be embedded in
a larger system it cannot fully access.
