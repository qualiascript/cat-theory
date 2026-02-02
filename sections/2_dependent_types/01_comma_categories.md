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
`B : D ^ I -> D * D`, `B M = (M 0, M 1)`. Then, let us define the comma category `F / G` as the pullback of `A` and
`B`. The name "comma category" is due to historical reasons, and it has little intuitive sense, but we use it for
consistency. Then for `Di : 1 -> C ^ D`, the cone category is `Diag_D / Di`, and the cocone category is `Di / Diag_D`.

