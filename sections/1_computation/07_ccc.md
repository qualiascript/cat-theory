# I.7. Cartesian Closed Categories

A category `C :: Cat` is considered Cartesian if it has all finite products. That is, for any `n :: FinSet`, there is
a functor `Prod_n : C ^ n -> C`. In particular, `Prod_0 : 1 -> C` implies it also has a terminal object. Products are
associative, that is, `(A * B) * C = A * (B * C)`. This can be seen due to the product in diagrams `a, b :: FinSet`
being equal to the product in diagram `a * b`, which can be shown by multiplying the number of induced morphisms in
the adjunction.

A Cartesian closed category, henceforth a CCC, is a Cartesian category that is closed. That is, if `C :: Cat`, it has
an internal homfunctor `hom : (op C) * C -> C`. All of `Cat`, `Set` and `FinSet` are CCCs. We have demonstrated the
product-exponent adjunction in `Cat`, however, since we have only used the existence of products and exponents, the
same logic can demonstrate it for a generic CCC.

As the product-exponent adjunction applies in any `C :: Cat` where C is a CCC. If we denote the terminal object as
`1`, we have that `(X ^ 1) ^ Y = X ^ (1 * Y) = X ^ Y`. As this applies for any `Y`, we have that `X ^ 1 = X`. In other
words, any morphism `f : 1 -> X` is isomorphic to a value `x :: X`.

## Evaluation map

In any CCC, consider the adjunction `hom(X * Y, Z) ~= hom(X, Z ^ Y)`. This is a natural bijection in `X` and `Z`, so
we can set `X = Z ^ Y`. Then we have `hom((Z ^ Y) * Y, Z) ~= hom(Z ^ Y, Z ^ Y)`. Consider the identity morphism
`id (Z ^ Y) : Z ^ Y -> Z ^ Y`. The natural bijection maps it to a morphism `f : (Z ^ Y) * Y -> Z`. As this morphism
always exists, we get a morphism `eval : (Z ^ Y) * Y -> Z`, called the evaluation map.

This tracks logically. Given an exponent object `Z ^ Y` and a value of `y :: Y`, one can always plug `y` into `Z ^ Y`
and get a new value, `z :: Z`. In the adjunction, we can also set `Z = X * Y` to obtain
`hom(X * Y, X * Y) ~= hom(X, (X * Y) ^ Y)`, and follow the bijection of the identity morphism to get a morphism
`coeval : X -> (X * Y) ^ Y`, which maps any object `x :: X` to an exponent object which takes argument `y :: Y` and
returns `x * y`. It is denoted the coevaluation map.

In fact, given any adjunction `hom_D(F x, y) ~= hom_C(x, G y)`, one can use a similar construction, applied to the
identity morphisms `id(G x)` and `id(F x)`, to get two natural transformations `unit : id D -> G F` and
`counit : F G -> id C`, where `id C, id D` are identity functors. The counit of the product exponent adjunction is the
evaluation map, and the unit is the coevaluation map. In a CCC, natural transformations are also morphisms.

## Simply typed lambda calculus

For any CCC, we now have equivalent constructions to currying, uncurrying and function evaluation. The similarity with
programming is, in fact, not coincidental. Consider `C :: Cat` a CCC. Let us use an alternative notation, so that for
`A, B :: C`, instead of `A ^ B` we write `B -> A`, and instead of `A * B` we write `(A, B)`.

Then, for a specific morphism `f :: A -> B`, it is defined by how it maps each `a :: A` to a `b :: B`. As such, to
denote a morphism, we can write the object it belongs to (referred to as a type annotation), and then write one or more
lines of form `f a = b`, meaning `a` gets mapped to `b`. The type annotation can be inferrable from context, in which
case it can be skipped. Let us write the terminal object as `()`, the product of zero terms.

Additionally, let us denote `\(a :: A) -> (b :: B)` a morphism from `a :: A` to `b :: B` which we do not give an
identifier name, potentially skipping the type annotations as well. This expression must be defined for all `a :: A`.
A morphism `f :: () -> X` is the same as picking some `x :: X`, so its body `f () = x` can be simplified to `f = x`.
If an identifier name is used in a type definition which hasn't been defined before, assume its type is any object
of `C`. However, during function application, it cannot be used to mean two different types.

Then let us consider a toy example `C :: Cat` to be a CCC defined as having the following objects: `FinSet` and the
set `Char` which contains all 255 ASCII characters, whose values are written in single quotes such as `'a'`. We know
that we always have a morphism `Eval :: (A -> B, A) -> B`, so instead of `Eval (f, x)` we write `f x`. Then we have:

```
Two :: FinSet
Two = 2

InfiniteString = FinSet -> Char
StringOfTwo = Two -> Char

Hi :: StringOfTwo
Hi 0 = 'H'
Hi 1 = 'i'

Curry :: ((A, B), C) -> A -> B -> C
Curry f = \x -> \y -> f (x, y)

Uncurry :: (A -> B -> C) -> ((A, B) -> C)
Uncurry f = \(x, y) -> f x y

Compose :: (X -> Y) -> (Y -> Z) -> (X -> Z)
Compose f g = \x -> g (f x)
```

This is a version of simply typed lambda calculus. It is not a Turing complete language, as it lacks recursion.
It can be made recursive by adding a morphism `Fix` so that `Fix f = f Fix f`, however its type definition cannot
be written directly in this language. In practice, most programming languages use more complex categories than CCC
for their architecture, but this syntax can also serve in being a more convenient way to talk about CCCs.

## Intuitionistic logic

A CCC can also serve as a model for intuitionistic logic, that is, a logical system that, unlike classical logic,
does not admit the law of excluded middle (`P OR NOT P`) and double negation (`NOT NOT P`). The correspondence lies
in taking `A * B` as `A AND B`, `A -> B` as `A IMPLIES B`, and the terminal element as `TRUE`. This link between
category theory, type theory and logical systems is known as the Curry-Howard-Lambek correspondence.
