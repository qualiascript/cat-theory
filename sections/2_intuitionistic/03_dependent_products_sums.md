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

## Dependent Product as Adjunction [NOTE : WIP]

We wish to derive the dependent product functor and check whether it is able to find the section families of a bundle.
We have `Bc_g : C / Y -> C / X`, which induces `DP_g : C / X -> C / Y` for some morphism `g : X -> Y`. The adjunction
property is `hom_{C / X}(Bc_g A, B) ~= hom_{C / Y}(A, DP_g B)`. On the left side, a morphism between `Bc_g a` and `B`
is given by a morphism `f : Bc_g a -> b` for `B : b -> X` so that `f . B = Bc_g a`. On the right side, morphisms are
given by `f' : a -> DP b` for `A : a -> Y` so that `f' . DP_g b = A`. 

We know that `Bc_g A : Pb(A, g) -> X`, so we have `f : Pb(A, g) -> b` so that `f . B = Bc_g a`. Practically speaking,
`Pb(A, g)` is the product of pairs of elements `(x, a') : 1 -> X * A` so that `x . g = a' . A`. Then `(x, a') . f`
sends the pair to some `e : 1 -> b` so that `e . B = (x, a') . Bc_g A = x` due to how pullbacks work. In other words,
`f` applied to `(x, a')` selects an element of the fiber of `X` at `x` for bundle `B`. Let us denote `q = a' . A`, then
for any `x` so that `x . g = q`, the homset on the left comprises morphisms that select an element of the fiber at `x`. 

Then going back to `hom(Bc_g A, B) ~= hom(A, DP_g B)`, the left side's property that `x . g = q` means that the values
of `x` are organized into fibers of `Y` through bundle `g`. Then for each fiber, each element `x` is mapped to an
element of `X` at fiber `x` through bundle `B`. Let us denote `B'` the bundle restricted to only the elements we
obtained, then denote `s = (x, a') . f`. Then, `s . B' = id`, a partial section restricted for each fiber of `Y`.

On the right side, recall that `A : a -> Y`. Then, a morphism from `A` to `DP_g B` is isomorphic to a family of partial
sections of `B` through the fibration `g`, as induced by the fibration of `A`. But recall that `A, DP_g B :: C / Y`,
so `DP_g B : R -> Y` and a morphism from `A` is some `D : a -> R`, so that we have an object and a morphism.


