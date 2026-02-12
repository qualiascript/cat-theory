# I.11. Monoids and Comonoids

A monoid is an F-algebra `m : 1 + X * X -> X`, meaning it has a unit element `i : X` and an operation `# : X * X -> X`
(which we will infix, so that `a # b = #(a, b)`). which respect the laws that `(a # b) # c = a # (b # c)`
(associativity) and `i # x = x # i = i` (unitality). It is an important algebra in category theory. An example of a
monoid can be constructed by setting `X = FinSet`, `i = 0`, `m : (a, b) -> a + b`. This is the monoid of natural numbers
with addition, and it can be trivially checked to respect the monoid laws.

Notice that the associativity and the unitality laws are respected by morphism composition. This suggests another monoid
construction, for some `M :: C`, set `X = hom(C, C)` in `a : 1 + X * X -> X`, alongside `i = id M`, `x # y = x . y`.
In other words, a monoid can be constructed from the set of endomorphisms of any object in a category, along with
morphism composition. In fact, an alternative definition is that a monoid is a category with a single object.

A monoidal category is given by an F-algebra `a : 1 + C * C -> C`, where `C :: Cat`, so that we have operations
`i :: C`, `# : C * C -> C` that respect the associativity and unitality laws. An example of a monoidal category is given
by the category of endofunctors `[D, D]`, with `i = id D` the identity endofunctor and `F # G = F . G` composition.

## Monoid in a Monoidal Category

Given a monoidal category `C :: Cat`, one can obtain a generalized conception of a monoid `M :: C` which instead of
using products, uses the `# : C * C -> C` operation of the category, which is also known as a tensor product, with a
suitable `1_C :: C` unit object. Note that in this case, the monoid is at the level of objects inhabiting `M`, not
`C`. Then, our F-algebra will look like `m : 1_C + M # M -> M`. In other words, we have unit `i : 1_C -> M` and
infix operation `a $ b`, respecting the laws `(a $ b) $ c = a $ (b $ c)` and `i $ a = a $ i = a`.

Considering the case of a monoid in the monoidal category of endofunctors, `M :: [C, C]` is an endofunctor whose
inhabitants `m :: M` are envisioned as objects `F c` for all `c :: C`. Then, we have a unit `i : 1_C -> M` and an
operation `$ : M # M -> M`, But `#` is functor composition, so the monoid is an endofunctor `M` with two natural
transformations `join : M . M -> M` and `unit : id C -> M`, so that `join(M . join(M . M)) = join(join(M . M) . M)`
and `join(unit . M) = join(M . unit) = M`. Such a monoid is known as a monad.

## List Monad

Let us consider `List A`, where `A :: C` and `C` is a CCC. Recall that `List A` is the initial algebra over the functor
`F : X -> 1 + A * C`. Then `List` can be envisioned as a function from `A` to the carrier of the initial algebra. We
have that `List f . List g = List (f . g)` by how algebra homomorphisms work, so `List` is an endofunctor in `C`.

Let us check if it is a monad. The natural transformation `unit : id C -> List` can be simply given component-wise as
`unit_X : X -> List X`, which embeds each `x :: X` into the list with `x` as its one element. Then,
`join : List . List -> List` component-wise is `join_x : List List x -> List x`. In order to obtain a list from a list
of lists, one can simply concatenate the lists successively. It can be trivially checked that the unitality and
associativity laws hold, thus, `List`, along with `unit` and `join`, forms a monad.

In fact, many practically useful endofunctors have suitable `unit` and `join` natural transformations so that they are
also monads. Oftentimes, a third natural transformation `bind` is used, which can be derived from the other two.
Its definition for monad `M` is `bind : (M a) * [a, M b] -> M b`, which can also be curried. It is obtained
by applying `unit` to `F: a -> M b` to obtain `F' : M a -> M M b`, then for `c :: M a`, returning the result
`c' = join(F' c) :: M b`. As such, a monad `M a` can be composed with any function `f : a -> M b`.

## Monads from Units of Adjunctions

The name collision between `unit` as a monad's natural transformation and `unit` as a natural transformation induced
by an adjunction is not accidental. Consider an adjunction `hom_D(F x, y) ~= hom_C(x, G y)`. Its unit is derived as
`unit : id D -> G F`, so we can name `M = G F`, which we need to show that it is a monad. The join operation is
`join : M . M -> M`, so `join : G F G F -> G F`. The components are `join_x : G F G F x -> G F x`. We can apply `F`
to get `F G F G F x`, and we also have `counit : F G -> id C`, which yields `F x`, which can turn to `G F x`.

Recall that an adjunction is a natural bijection of homsets. Given any `g : x -> G y`, getting its equivalent
`f : F x -> y` and then going back must yield the same result. Units are derived from applying this construction to
`id (G y)`, so `id (G y) . unit = id (G y)`. As this is a natural bijection, this applies to any value of `y`, thus,
`G . unit = id G`. Similarly, `counit . F = id F`. Using this fact, known as the triangle identities, the monad laws
become trivial to check. In fact, any `unit` and `counit` that follow the triangle identities induce an adjunction.

The unit of the product-exponent adjunction is the coevaluation map `coeval : X -> (X * Y) ^ Y`. Thus, another example
of a monad is `M X = (X * Y) ^ Y`, for any value `Y`. This is known as the state monad, `State Y X = [Y, X * Y]`.
As such, its inhabitants `f :: State Y X` are morphisms `f : Y -> X * Y`. By embedding a value `x :: X` in a state
monad, for instance `MyState = State Y`, one is able to `bind` it to morphisms `g : X -> MyState Z` which are able
to modify or utilize the value of `y :: Y` without explicit handling. This is how functional programming handles state.

## Comonoids and Comonads

Monads have a dual concept known as Comonads. A Comonoid in a Monoidal Category `C :: Cat` is the same as a monoid
in the opposite category `op C`. Alternatively, it is an F-coalgebra of the form `a : C -> 1 + C # C`, where `#`
is `C`'s tensor product. A comonad `W`, then, is a comonoid in a monoidal category of endofunctors. This induces
two natural transformations, `counit : W -> id C` and `cojoin : W -> W . W`. Comonoids follow dual laws compared to
monoids, known as coassociativity and counitality.

Similarly to monads, it is often helpful to define a cobind natural transformation, `cobind : (W a) * [W a, b] -> W b`.
The evaluation map `eval : (Z ^ Y) * Y -> Z` is a counit, and as such, it induces a comonad, known as the store or
costate comonad `Store Y X = Y * [Y, X]`. This illustrates the usage of comonads as handling many potential options
from which one can extract one in particular.