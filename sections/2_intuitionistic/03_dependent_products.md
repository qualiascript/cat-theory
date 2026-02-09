# II. 3. Dependent Products

Let `C :: Cat` be a complete category and `a :: C ^ I`, `a : x -> y`. Considering the category `C / y`, one of its
elements is `a`. We would like to create a functor `F : C / y -> C / x`, known as the base change functor. Given
a bundle `p: k -> y` of `C / y`, we would like to map it to a bundle of `C / x`, `p': k' -> x`. We also know the
morphism `a : x -> y`, which forms a cospan with `p : k -> y`. Then, the pullback `Pb(a, p)` induces two projections
`p': Pb(a, p) -> x`, `q: Pb(a, b) -> k` so that `p' . a = q . p`. Then, let `F` map `p` to `p'`.

Intuitively, we have a bundle `p : k -> y`, and we would like to change the base of the slice category to be `x`.
Given that we are only given a morphism `a : x -> y`, we seek to find the universal construction that corresponds
to the bundle `p` viewed from the perspective of `a`. This is similar to a fiber of `p`, but for all elements
encompassed in the bundle `a`. As such, pullbacks are also referred to as fiber products. One can check that
`Bc : C / y -> C / x` also maps morphisms respecting functor laws, and as such, it is the base change functor.

## Sections

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
that `S` is a local section of `B` over a specific fiber. Then, `hom(Bc_g A, B)` is a family of local sections.

As such, `hom(A, DP_g B)` is isomorphic to a family of local sections of `B` for each fiber in the space of `Y`
which is obtained by restricting the bundle `g` to values parametrized by `A`. But recall that `DP_g B :: C / Y`,
so that a morphism from `A : a -> Y` to `DP_g B : R -> Y` corresponds to a morphism `M : a -> R`, with the property
that `M . (DP_g B) = A`. If we set `A = id Y`, we get that `M . (DP_G B) = id Y`, so that `M` is a section of
`DP_g B`. Then, the sections of `DP_g B` are isomorphic to local sections of `B` indexed by all fibers of `g`.

Thus, `DP_g B : R -> Y` itself must correspond to a mapping, which sends the local sections of `B` to the fiber of
`g` it corresponds to. As such, its sections pick an element from each such fiber, so that the family of sections
consists of the family of all such local sections of `B` indexed by `g`. In particular, if `g : X -> 1`, this reduces
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

Consider the bundle `A : List FinSet -> FinSet`, which indexes each list of integers by its size, known as a dependent
type. This naturally induces `B = A * A : (List FinSet) * (List FinSet) -> FinSet * FinSet`. Then consider the function
`g : FinSet * FinSet -> FinSet`, `g a b = a + b`. Then, the dependent sum `DS_g B` is a mapping of pairs of lists of
integers by their added sizes, of the form `H : (List FinSet) * (List FinSet) -> FinSet`. This demonstrates the
properties of dependent sums, in using morphism composition to construct new indexed types.

Going back to `A : List FinSet -> FinSet`, consider the effect of the base change functor induced by
`g : FinSet * FinSet -> FinSet` at `A`. It is given by `A' : Pb(A, g) -> FinSet * FinSet` so that for pairs
`a', (x, y) :: List FinSet * (FinSet * FinSet)`, we have `a' . A = x . g`. In other words, the length of `a'` equals
`x + y`. Thus, `A'` is the dependent type of lists indexed on two integers whose sum is the size of the list. This
demonstrates the practical use of the base change functor, as substitution of a dependent type's indexing.

Let us denote this as `Vec (a + b)` for simplicity. By similar logic, if `C / FinSet * FinSet` is a CCC, we can obtain
the bundle `B = [(Vec a) * (Vec b), Vec (a + b)]`. Then, for `g : FinSet * FinSet -> 1`, consider `DP_g B`. Given that
there is only one fiber of `g`, it is a mapping of each element of `z :: FinSet * FinSet` to an element of `B` at the
corresponding `z` fiber. In other words, it is the family of morphisms `m : (Vec a) * (Vec b) -> Vec (a + b)` so that
the addition property is respected in each list.

In fact, for `g' : FinSet * FinSet -> FinSet`, `g' a b = a * b`, consider `DP_g' B`. The fibers of `g'` consist of
values `n :: FinSet` so that `a * b = n`, and for each such fiber, the same family of morphisms is constructed. As
such, it is a family of morphisms `m : (Vec a) * (Vec b) -> Vec (a + b)` for each `n :: FinSet` so that `a + b = n`.
This demonstrates the properties of dependent products, in terms of generalizing the concept of internal homsets for
situations where morphisms must fulfill additional requirements related to their indexing.