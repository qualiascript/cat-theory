# Cartesian Closed Categories

A category `C :: Cat` is considered Cartesian if it has all finite products. That is, for any `n :: FinSet`, there is a
functor `Prod_n : C ^ n -> C`. In particular, `Prod_0 : 1 -> C` implies it also has a terminal object. Products are
associative, that is, `(A * B) * C = A * (B * C)`. This can be seen due to `Prod_2(Prod_x(a), Prod_y(b)) = Prod_(x*y)(a*b)`,
which can be shown by multiplying the number of induced morphisms in the adjunction.

A Cartesian closed category, henceforth a CCC, is a Cartesian category that is closed. That is, if `C :: Cat`, it has
an internal homfunctor `hom : (op C) * C -> C`. All of `Cat`, `Set` and `FinSet` are CCCs. We have demonstrated the
product-exponent adjunction in `Cat`, however, since we have only used the existence of products and exponents, the
same logic can demonstrate it for a generic CCC.

## Evaluation map

In any CCC, consider the adjunction `hom(X * Y, Z) ~= hom(X, Z ^ Y)`. This is a natural bijection in `X` and `Z`, so we
can set `X = Z ^ Y`. Then we have `hom((Z ^ Y) * Y, Z) ~= hom(Z ^ Y, Z ^ Y)`. Consider the identity morphism
`id (Z ^ Y) : Z ^ Y -> Z ^ Y`. The natural bijection maps it to a morphism `f : (Z ^ Y) * Y -> Z`. As this morphism
always exists, we can define a natural transformation `eval : (Z ^ Y) * Y -> Z`, called the evaluation map.

This tracks logically. Given an exponent object `Z ^ Y` and a value of `y :: Y`, one can always plug `y` into `Z ^ Y`
and get a new value, `z :: Z`. In the adjunction, we can also set `Z = X * Y` to obtain
`hom(X * Y, X * Y) ~= hom(X, (X * Y) ^ Y)`, and follow the bijection of the identity morphism to get a natural
transformation `coeval : X -> (X * Y) ^ Y`, which maps any object `x :: X` to an exponent object which takes
argument `y :: Y` and returns `x * y`. It is denoted the coevaluation map.

In fact, given any adjunction `hom_D(F x, y) ~= hom_C(x, G y)`, one can use a similar construction to get two natural
transformations `unit : id D -> G F` and `counit : F G -> id C`, where `id C, id D` are identity functors. The counit
of the product exponent adjunction is the evaluation map, and the unit is the coevaluation map.

## Simply typed lambda calculus

For any CCC, we now have equivalent constructions to currying, uncurrying and function evaluation. The similarity with
programming is, in fact, not coincidental.

[TO BE CONTINUED]
