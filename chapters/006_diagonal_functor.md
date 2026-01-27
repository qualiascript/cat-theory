# Diagonal functor

Recall that every `D :: Cat` induces a functor `F :: [C, 1]` that collapses the category to `1`. Furthermore,
for any `C :: Cat`, `C = C ^ 1 = [1, C]`. This is a functor category in natural isomorphism to `C`, and as such,
the objects `c :: C` fully characterize the functor `c :: [1, C]`. This can be seen as a functor that maps the unique
object of `1` to `c`, and the identity morphism of `1` to `id c`.

Picking two objects from `[D, 1]` and `[1, C]`, they can be composed to `Const :: [D, C]`, `Const d = c`. In fact,
`c :: C` can also be taken as an argument, as to get an object of `[C * D, C]`, as `Const c d = c`. By the product
exponent adjunction, this is naturally isomorphic to `diag_D :: [C, [D, C]]`, which we will denote a D-ary diagonal
functor. It sends each category `C :: Cat` to a constant functor in `[D, C]`, by sending any `c :: C` to
`Const c d = c`, and any `f :: C ^ I` to `Const c f = id c`.

If `D, C :: Cat` `Di :: C ^ D` represents a method of mapping each `d :: D` to `Di d :: C` and each
`f :: D ^ I` to `Di f :: C ^ I`. If `D` is sufficiently small, this can be visualized by drawing all objects and
morphisms of `D` and labeling them by the object they get sent to in `C`. This is a diagram! As such, let us denote
`Di :: C ^ D` as a diagram of shape D in C. It is exactly the same as a functor in `[D, C]`, but the diagram
perspective comes in handy in specific contexts.

## Cones and Cocones

Then, objects of `[C, C ^ D]` send each `c :: C` to a constant diagram `Di :: C ^ D`, which maps each object
`d :: D` to `c :: C` and each morphism `f :: D ^ I` to `id c :: C ^ I`. Let us now consider the meaning of
a natural transformation in `alpha :: [C, C ^ D] ^ I`, with `alpha : Diag_D -> F`. `alpha_x` maps
`Diag_D x :: C ^ D` to `F x :: C ^ D`. Let us draw the naturality condition for `f :: C ^ I`, `f : x -> y`:

```
  Diag_D x -- Diag_D f -→ Diag_D y
  |                       |
  |                       |
alpha_x               alpha_y
  |                       |
  ↓                       ↓
  F x ------- F f ------→ F y
```

Recall that `Diag_D x` is a diagram `Di :: [D, C]` so that for any `d :: D`, `Di d = x`, and for any `f :: D ^ I`,
`Di f = id x`. Then let's draw the naturality condition for any `d :: D`, which lands us back in `C`.

```
   x ------ id x -----→ x
   |                    |
   |                    |
alpha_x d            alpha_y d 
   |                    |
   ↓                    ↓
   F x d --- F f d --→ F y d
```

Then for all `d :: D`, `(alpha_x d) . (F f d) = (id x) . (alpha_y d)`, which simplifies to
`alpha_y d = (alpha_x d) . (F f d)`. So we have that for any `d :: D`, `alpha_y d :: C`, `alpha_y d : x -> F y d`.
Then, `alpha` can be seen as a function that maps each `c :: C` to a set of maps `alpha_c` from all `d :: D` to some
`F c d :: C`. Let us name `Di = F c :: C ^ D`. As each `c` lands back in `C`, this can be  simplified into a set of
morphisms from `c` to `Di b`, for all `b :: D`.

Recall that `F :: [C, C ^ D]`, so `alpha_y :: [D, C] ^ I` is also a natural transformation. As such, for any morphism
`f :: D ^ I`, `f : x -> y`, `alpha_c y = (alpha_c x) . (F c f)`. This implies the diagram `Di = F c :: C ^ D` has the
property that if `f, g :: D ^ I`, `f, g : x -> y`, then `Di f = Di g`. In other words, all morphisms between any two
given objects are equal. A diagram `Di` that follows this property is denoted a commutative diagram.

We then say that `alpha_c :: (C ^ D) ^ I` is a cone with apex `c :: C`, base `Di :: C ^ D` a commutative diagram, and a
set of morphisms for any `C :: C`, as `f : d -> Di d`. By looking at `beta : F -> Diag_D` instead, one obtains the dual
concept of a cocone, whose morphisms go `f : Di d -> d`.

## Adjunctions of the Diagonal Functor

We now have a diagonal functor `Diag_G : C -> C ^ D`, and we know that it's part of a functor category `[C, [D, C]]`,
so that its outbound morphisms are cones and its inbound morphisms are cocones. Let us now consider what its right
adjoint would be. It is by necessity a functor `F : C ^ D -> C`

We have `hom_{C^D}(Diag_D x, y) ~= hom_C(x, F y)`. This is a bijection between sets of morphisms, but the left side
is also equivalent to a set of cones. In other words, `F` maps a diagram `y :: C ^ D`, which selects objects and
morphisms in `D`, to a value `c :: C` with the property that for any other `x :: C`, there is a morphism `f :: x -> c`
exactly for each cone with apex `x` and diagram `y`. Recall that a cone with apex `x` and diagram `y` represents a
set of morphisms from `x` to all objects in `y a` where `a :: C`, so that the diagram commutes.

To simplify, for any commutative diagram `y :: C ^ D`, `F y` is the object with the property that each morphism from
`x :: C` to `F y` is equivalent to a family of morphisms from `x` to the objects which `y` picked in `C`. `F` is called
the limit functor `Lim : C ^ D -> C`, and `Lim y` is called a limit.

By instead looking at the left adjoint of the diagonal functor, we can show it to be the colimit functor
`Colim : C ^ D -> C`. It has the property that a morphism from `Colim x` to any object `y :: C` is equivalent
to a family of morphisms from the objects picked by commutative diagram `x :: C ^ D` to `y`.

## Products and Coproducts

In order to illustrate limits and colimits, it is helpful to pick a specific category `D`. Let's set `D = 2` and
`C = Set`. The diagonal functor is then a map from each `x :: Set` to a functor that sends each object of `2`
to `x`. This is the same as a pair, meaning `Diag_2 x = (x, x)`.

Then, we have `hom-{C^2}((x, x), (a, b)) ~= hom(x, Lim(a, b))`. The left side comprises families of morphisms from
`(x, x)` to `(a, b)`, which is the same as pairs of morphisms `f : x -> a`, `g : x -> b`. Then, we have that each
morphism `h : x -> Lim(a, b)` must correspond exactly to a pair of morphisms to each of `a`, `b`. Recall that we
are in `Set` and morphisms are functions. Thus, we get the property: there is a function from any set `x` to
`Lim(a, b)` if and only if there are two functions from `x` to `a` and from `x` to `b`. This means
`Lim(a, b) = a * b`, the Cartesian product of the two sets. 

This property can be generalized to other categories as well, and as such we denote `Lim(a, b)` to be the product
of `a, b :: C`, if it exists. Within `Cat`, it is the previously defined product category. Within `FinSet`,
the product of two natural numbers is the result of multiplication.

Let us also consider `Colim(a, b) :: Set`. By analogy, it is the set so that, for any other `x :: Set`, there is a
function from `Colim(a, b)` to `x` if and only if there are two functions from `a` to `x` and from `b` to `x`.
This is the case when `Colim(a, b)` is a disjoint union of `a` and `b`, which includes all elements from both `a`
and `b` while keeping track what set they originate from, so that the functions don't collide.

In general terms, for `a, b :: C`, `Colim(a, b)` is called their coproduct. In general, if a limit is given a name,
the colimit will have the same name prefixed with "co-". In `Cat`, the coproduct of two categories creates a new
category with all the objects and morphisms of each and no morphisms between any objects originating from different
categories. In `FinSet`, the coproduct of two natural numbers is called addition.

## n-ary Products and Coproducts

In fact, the definition of products and coproducts can be expanded further, from `2` to any diagram originating in
`n :: Set`. The same underlying logic applies, but each morphism is bijective to a set of morphisms with the same
cardinality as `n`. It is alternatively equivalent to iterated products and coproducts. We denote it n-ary products
and coproducts. If `n :: FinSet`, they are additionally finite product and coproducts. If `n = 1`, the products and
coproducts can be trivially shown to be equal to the selection of object.

Let us also consider the case for `n = 0`. A product of zero objects is the object `c :: C` with the property that, for
each morphism from an object `n :: C` to it, there is a cone with apex `n` and diagram `0`. That cone is in category
`[C, C ^ 0] ^ I = [C, 1] ^ I = 1 ^ I = 1`. In other words, for any `n`, there is exactly one morphism to the empty
product. As such, it is called the terminal object. Similarly, the initial object of a category is the result of a
colimit over the diagram `0`. It has exactly one outbound morphism to any other object.

In `Cat`, the initial object `x` is the object so that for any `C :: Cat`, we have `[x, C] = 1`. Observe that the
solution is `x = 0`. The terminal object has the property that for any `C :: Cat`, `[C, y] = 1`. Observe that `y = 1`.
Analogous logic shows that this also applies to  `Set` and `FinSet`.
