# II. 3. Dependent Products and Sums

Consider a bundle `f: A -> B`, `f :: C ^ I`. Given a global element `X : 1 -> B`, one can perform a fiber product of
`f` and `X` to obtain a fiber of the bundle. This fiber `fb : Pb(f, X) -> B` maps all elements to `X`. We have that
for any `S : B -> Pb(f, X)`, if `H = X . S : 1 -> (Pb(f, x) ^ B)`, so `H : B -> Pb(f, X)`, `H . fb = id B`. That is,
`H` is a right inverse for `fb`, as the action of `S` is restricted over `X`, and any mapping from `X` to any object
of `Pb(f, X)` will return back to `X`. 

This suggests that if bundle `f : A -> B` is an indexing of `a :: A` to `b :: B`, any right inverse `S : B -> A`,
`S . f = id B` represents a mapping of `b :: B` to `a :: A` so that `a` is mapped by `f` to `b`. This is known as a
section of the bundle, and the family of all sections of a bundle by necessity maps `b` to all values `a` which map
back to `b`. This implies that, given a bundle which indexes objects, one ought to look for its family of sections
in order to obtain the indexing from the perspective of the object the bundle is an element of.

Let us consider the family of sections of a bundle. Consider the bundle `f : [X, Y] -> 1`. Its sections will be
`s :: [X, Y]`, and, in fact, for any `s`, `s . f = id 1`, so the family of bundles is the internal homset. This is
also the case for `f' :: [X * Y, Y]`, `f' x y = y`, as the only section of identity is itself. But notice that `X * Y`
as a product is also a fiber product, specifically of `X' : X -> 1` and `Y' : Y -> 1`. As such, `f' : Pb(X', Y') -> Y`.

Recall that the base change functor `Bc : C / b -> C / a` induces by `h : a -> b` maps a morphism `k : z -> b` to
`k': Pb(k, h) -> a`. Working backwards, this suggests `Bc : C / 1 -> C / Y`, induced by `Y': Y -> 1`, applied to
`X' : X -> 1`, yields `f' : Pb(X', Y') -> Y`. We also know that `f' :: [X * Y, Y]`, and since the `Y` value is uniquely
determined, `f' ~= X * Y`. Its family of sections is `[X, Y]`. In other words, specifically in this instance, we find
that the right-adjoint of `Bc`, which we will denote the dependent product `DP`, finds the family of sections.

## Dependent Product as Adjunction

We wish to derive the dependent product functor and check whether it is able to find the section families of a bundle.
We have `Bc_g : C / Y -> C / X`, which induces `DP_g : C / X -> C / Y` for some morphism `g : X -> Y`. The adjunction
property is `hom_{C / X}(Bc_g A, B) ~= hom_{C / Y}(A, DP_g B)`. On the left side, a morphism between `Bc_g A` and `B`
is given by a morphism `f : Bc_g A -> b` for `B : b -> X` so that `f . B = Bc_g A`. On the right side, morphisms are
given by `f' : a -> DP b` for `A : a -> Y` so that `f' . (DP_g B) = A`. 

We know that `Bc_g A : Pb(A, g) -> X`, so we have `f : Pb(A, g) -> b` so that `f . B = Bc_g a`. Practically speaking,
`Pb(A, g)` is the product of pairs of elements `(x, a') : 1 -> X * A` so that `x . g = a' . A`, which we will denote
`q`. Then `(x, a') . f` sends the pair to some `e : 1 -> b` so that `e . B = (x, a') . Bc_g A = x`. This means each
`(x, a')` is mapped by `f` to some `e` which is in the fiber of `B` at `x`. However, given a specific value of
`q : 1 -> Y`, the mapping is only done for values so that `x . g = q`. 

Let us name `H = Bc_g A . g : Pb(A, g) -> Y`. Then we can rephrase this as such: for each of the fibers of `H` at some
`q`, `f` is a selection for all `x :: X` in the fiber product to an element `e` of `B` at the fiber of `B` at `x`.
Then let us denote `B' : b' -> x'` the morphism `B` restricted to only the elements picked by a specific mapping `f`
stemming from a specific fiber `X' : 1 -> x'`. Then denote `S = X' . f : x' -> b'`. We have that `S . B' = id b'`, so
that `S` is a partial section of `B` over a specific fiber. Then, `hom(Bc_g A, B)` is a family of partial sections.

As such, `hom(A, DP_g B)` is isomorphic to a family of partial sections of `B` for each fiber in the space of `Y`
which is obtained by restricting the bundle `g` to values parametrized by `A`. But recall that `DP_g B :: C / Y`,
so that a morphism from `A : a -> Y` to `DP_g B : R -> Y` corresponds to a morphism `M : a -> R`, with the property
that `M . (DP_g B) = A`. If we set `A = id Y`, we get that `M . (DP_G B) = id Y`, so that `M` is a section of
`DP_g B`. Then, the sections of `DP_g B` are isomorphic to partial sections of `B` indexed by all fibers of `g`.

Thus, `DP_g B : R -> Y` itself must correspond to a mapping, which sends the partial sections of `B` to the fiber of
`g` it corresponds to. As such, its sections pick an element from each such fiber, so that the family of sections
consists of the family of all such partial sections of `B` indexed by `g`. In particular, if `g : X -> Y`, this reduces
to all mappings of elements of `X` to sections of `B`, and if `B : B' * X -> X` ignoring the first argument (known as 
a trivial bundle), then its sections are simply `B'`, so that we obtain `R = [X, B']`.

## Dependent Sums

Dependent sums, denoted `DS`, are the left adjoint of the base change functor, `hom(DS_g A, B) ~= hom(A, BC_g B)`.
On the right side, we have morphisms `f : a -> PB(B, g)` for `A : a -> X` so that `f . (BC_g B) = A`. Then for
`g : X -> Y`, `B : b -> Y`, the pullback selects elements `(x, b') :: X * B` so that `x . g = b' . B`. Then, `f`
composes each `a' : 1 -> a` with a `(x, b')`, which we can denote `(ax, ab')`, so that `ax . g = ab . B`. Then,
`a' . f . (BC_g B) = a' . A`, so that `ax = a' . A`, meaning `a' . A . g = ab . B`.

Then, `hom(DS_g A, B)` is isomorphic to a family of morphisms `f` that for each `a' :: a` select an `ab :: b` so that
`a' . A . g = ab . B`. In particular, if we select `B = id Y`, this sends each `a' :: a` to `ab = a' . A . g`. A
morphism from `DS_g A` to `id Y` is given by `M : a -> Y` so that `M . (id Y) = DS_g A`. Then, in general, the action
of `DS_g A` is to send each `a' :: a` to `a' . A . g`. In other words, for any `A :: C / X`, `DS_g A = A . g`.

## Dependent Products and Sums Intuition

[TO BE CONTINUED]