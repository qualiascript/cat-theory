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

A comma on `C` can be conceptualized as a subcategory of the arrow category `C ^ I`. Then, a morphism in the
comma category is a natural transformation simply given by its effect on the underlying two objects and the unique
non-trivial morphism. If `f : A -> B`, `f' : A' -> B'` are objects of `F / G`, with `F :: [C, D]`, `G :: [E, D]`,
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
represent the best possible approximation in the category. As we'll see, this applies to many other constructions.

## Slice Category

A specific type of comma category is given by a functor `F :: [1, C]`, which selects a `c :: C`, and the identity
functor `id C :: [C, C]`. Then, the comma category `id C \/ c` is also known as the slice category `C / c`. It is
the category of morphisms whose destination is `c`. A morphism in the slice category between two objects
`a : x -> c`, `b : y -> c` is given by a morphism `i : x -> y` so that `i . b = a`. There is a dual coslice category
`c / C`, which is the category of morphisms whose origin is `c`.

Recall that the morphisms inbound into an object can be thought of as their generalized elements. This is exactly what
the slice category consists of. Really, each morphism could correspond to multiple elements, unless the origin is the
terminal object, and as such it is referred to as a bundle. A bundle could map multiple elements of an object to the
same element in the destination. One can obtain the elements mapped to a point, as a morphism from the terminal object,
known as a global element, by doing a pullback with the bundle. This is known as the fiber over the point.

## Base Changes

[TO BE CONTINUED]
