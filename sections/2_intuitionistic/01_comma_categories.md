# II.1. Comma Categories

Recall our definition of a cone: it consists of an apex, a diagram and morphisms from the apex to the diagram which
induce commutativity. It will come in handy to generalize this construction. In particular, notice that the reason
we only have morphisms coming from an apex is because `cone :: [D, C] ^ I` is a natural transformation whose starting
point is the constant functor `Const :: [D, C]`, `Const d = c` for some cone `c`. We seek to extend the concept of
a cone to non-constant functors.

Then, we have two functors `F :: [D, C]`, `G :: [E, D]` and we seek to create a category so that for any `x :: C` we
have that `F x` is a cone, that is, it incudes morphisms from `F x` to all `G y` for `y :: C` so that the diagram
commutes.But recall where the condition of commutativity emerged from in the first place: the components of the natural
transformation `alpha_y :: [D, C] ^ I` are themselves natural transformations. This is induced automatically if we have
`F, G :: [C, D ^ C]`, as such, let us remove the commutativity condition.

Then, we simply have two functors `F :: [C, D]`, `G :: [E, D]` and we wish to construct the category of morphisms
`a : F x -> G y`, for any `x, y :: C`. Notice that if instead the condition was `F x = G y`, this would induce a
pullback. Instead, we have two equality conditions: `F x` must equal the starting point and `G y` must equal the
destination of a morphism. In other words, in the morphism category `D ^ I`, if we denote the initial object of `I`
as `0` and the terminal object as `1`, we have that for `M :: D ^ I`, `M 0 = F x`, `M 1 = G y`.

Notice that by using products, we can denote this as `(F x, G y) = (M 0, M 1)`, and we want all objects with this
property. We have a pullback! Construct the functors `A : C * E -> D * D`, `A (x, y) = (F x, G y)` and
`B : D ^ I -> D * D`, `B M = (M 0, M 1)`. Then, let us define the comma category `F \/ G` as the pullback of `A` and
`B`. The name "comma category" is due to historical reasons, and it has little intuitive sense, but we use it for
consistency. Then for `Di : 1 -> C ^ D`, the cone category is `Diag_D \/ Di`, and the cocone category is `Di \/ Diag_D`.

## Terminal Cone

A comma category on `C` can be conceptualized as a subcategory of the arrow category `C ^ I`. Then, a morphism in the
comma category is a natural transformation simply given by its effect on the underlying two objects and the unique
non-trivial morphism. If `f : A -> B`, `f' : A' -> B'` are objects of `F \/ G`, with `F :: [C, D]`, `G :: [E, D]`,
a morphism in the category is given by two morphisms `F a: A -> A'`, `G b: B -> B'` so that `F a . f' = f . G b`.
Note that the morphisms are in the image of the functor in order to ensure their existence in the subcategory.

Let us now look at the category of cones `Diag_D \/ Di`. Limits are given by the adjunction
`hom_{C^D}(Diag_D x, y) ~= hom_C(x, Lim y)`, where the left side is exactly a set of cones with apex `x` and diagram
`y`. In other words, each morphism `a : x -> Lim y` is in bijection with a cone. Let us consider the morphism
`id(Lim y) : Lim y -> Lim y`, which induces a cone with apex `Lim y`. Morphisms in the cone category from apex `a`
to `Lim y` are morphisms `a : x -> Lim y`, so they're in bijection with the cones themselves, so they are unique.

In other words, `Lim y` is the apex of the terminal cone. Similarly, `Col y` is the apex of the initial cocone. This
demonstrates what is meant by limits and colimits having a universal property: any cone has a unique morphism to the
universal object in question. If cones are seen as potential approximations of a result, limits and colimits
represent the best possible approximation in the category.

## Universal constructions

Consider `F -| G`, `F : C -> D`, `G : D -> C`, so that `hom_D(F a, b) ~= hom_C(a, G b)`. This is a natural bijection,
so it induces a natural isomorphism of comma categories `F \/ id D ~= id C \/ G`. Then, for any `x :: D`, a terminal
object in `F \/ x` is isomorphic to a terminal object in `id C \/ G x`. The terminal object is given by `id(G x)`,
as morphisms in the comma category are exactly `hom_C(x, G x)`. As such, the right side `hom_C(G x, G x)` is
isomorphic on the left with `hom_D(F G x, x)`, which is our `counit` natural transformation.

We also have that `F \/ x` always has an initial object for any `x :: D`. It is given by `id(F x)`, so that we have
`hom_D(F x, F x)` isomorphic to `hom_C(x, G F x)`. This gives us our `unit` operation, so `counit` is sufficient
to create the adjunction. Thus, if `F \/ x` has a terminal object for all `x :: D`, or in other words, `F \/ id D`
has a terminal object, it has a right adjoint. In fact, the two concepts are naturally isomorphic both globally for
`F` and for any `F x`. By similar logic, if `id C \/ G` has an initial object, it is the left adjoint of `G`.

Also consider the Yoneda lemma, `hom(Yo c, Pr) ~= Pr c`. Let us take `Yo : C -> [op C, Set]`, `Pr : 1 -> [op C, Set]`
and create the comma category `Yo \/ Pr`. Objects in this category are given by `f : Yo a -> Pr`, so by the Yoneda
Lemma, `f :: Pr a`. Let us state `f` is the terminal object. A morphism from `g :: Pr b` to `f` is given by
`m : Yo b -> Yo a`, so `m : a -> b` which is unique. Then `Pr b ~= hom(Pr b, f) ~= hom(a, b)`, and since this
is for any `b`, `Pr ~= hom(a, -)`. Thus, if `Yo \/ Pr` has a terminal object, `Pr` is representable.

This demonstrates that the universal property of various categorical objects, such as limits, colimits, adjunctions
and representable presheafs, share in common that they can be characterized in terms of comma categories. This suggests
that they could be generalized to a more generic construction which encodes the idea of a universal property.
As we will later see, all these concepts are instances of what is known as Kan extensions.

## Slice Category

A specific type of comma category is given by a functor `F :: [1, C]`, which selects a `c :: C`, and the identity
functor `id C :: [C, C]`. Then, the comma category `id C \/ c` is also known as the slice category `C / c`. It is
the category of morphisms whose destination is `c`. A morphism in the slice category between two objects
`a : x -> c`, `b : y -> c` is given by a morphism `i : x -> y` so that `i . b = a`. There is a dual coslice category
`c / C`, which is the category of morphisms whose origin is `c`. Additionally, `C / 1 = 1 / C = C`.

Recall that the morphisms inbound into an object can be thought of as their generalized elements. This is exactly what
the slice category consists of. Really, each morphism could correspond to multiple elements, unless the origin is the
terminal object, and as such it is referred to as a bundle. A bundle could map multiple elements of an object to the
same element in the destination. One can obtain the elements mapped to a point, as a morphism from the terminal object,
known as a global element, by doing a pullback with the bundle. This is known as the fiber over the point.

## Base Changes

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
