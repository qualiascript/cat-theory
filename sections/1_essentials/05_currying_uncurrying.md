# Chapter 5: Currying and Uncurrying

Recall the homfunctor `hom : (op C) * C -> Set`. We have previously claimed that one can "fix" either the first
or the second value in the product category in the domain and obtain a new functor. More generally, given a functor
`F :: [X * Y, Z]`, there is a function `alpha` with domain `X` and codomain `[X * Y, Z] ^ I`, so that we have a
natural transformation `alpha x :: [X * Y, Z] ^ I` for each `x :: X`. This is a categorization of the idea of "fixing"
`x :: X` in the original functor.

We can define `alpha x` component-wise: for each object `(x', y) :: X * Y`, one obtains `F (x', y) :: Z`. Then, we
define `(alpha x)_x' :: Z ^ I`, `(alpha x)_x' : F (x', y) -> F (x, y)`. It can be checked that this fulfills the
naturality conditions.

Let's then denote `G :: [X, [X * Y, Z]]`, `G (x) (x', y) = F (x, y)`. As the value of `x' :: x` is unused, 
`G x :: [X * Y, Z]` can be shown to be naturally isomorphic to `H :: [Y, Z]`. As such, we can simplify the object
to `G :: [X, [Y, Z]]`. Then, we have a function that takes a functor `F :: [X * Y, Z]`, and obtains a functor
`G :: [X, [Y, Z]]`.

We can also build the inverse function. Given any `G :: [X, [Y, Z]]`, we can build the object `X * Y`, as well as
functors `first :: [X * Y, X]`, `first (x, y) = x`, `second :: [X * Y, Y]`, `second (x, y) = y`. Then for any
`z :: X * Y`, `G (first z) (second z) = Z`. This constitutes a functor `F :: [X * Y, Z]`.

Since we have an invertible function that maps any `F :: [X * Y, Z]` to `G :: [X, [Y, Z]]`. Alternatively, they can be
denoted as `F :: Z ^ (X * Y)` and `G :: (Z ^ Y) ^ X`. Recall that functor categories are equivalent to internal
homsets of `Cat`. So for functor `hom : (op Cat) * Cat -> Set`, we have a bijection between `hom(X * Y, Z) :: Set` and
`hom(X, Z ^ Y) :: Set`.

In other words, `hom(X * Y, Z) = hom(X, Z ^ Y)`, which is known as the product-exponent adjunction. It is the category
theory definition for currying and uncurrying. Currying is the process of transforming an object of the form
`a : X * Y -> Z` into an object `b : X -> [Y, Z]`, and uncurrying is the reverse operation.

## Natural Bijection

In fact, we have an even stronger condition. Consider the functors `homL, homR :: [X * Z, Set]` with the values
`homL (X, Y) = hom(X * Y, Z)` and `homR (X, Y) = hom(X, Z ^ Y)`. There is a bijection between `homL a` and
`homR a` for any `a`, and the naturality condition can also be trivially checked. As such, `homL = homR`.
We also write it as `hom(X * Y, Z) ~= hom(X, Z ^ Y)` and denote it a natural bijection.

As `hom(X * Y, Z) ~= hom(X, Z ^ Y)`, and the internal homset in `Cat` is functor categories, we can also derive that
`Z ^ (X * Y) ~= (Z ^ Y) ^ X`.

## Products and Exponents in `FinSet`

Since this applies in `Cat`, it applies in its subcategory `FinSet` as well. recall that the objects of `FinSet` are
natural numbers. If `A, B :: Set`, `A * B` is the Cartesian product, whose cardinality is the product of `A` and `B`.
`A ^ B` has to send every `b :: B` to some `a :: A`. In other words, it must make a selection of `a` exactly `B` times.
As such, `A ^ B` is equivalent to the product of `A` with itself `B` times. This is natural number exponentiation.
We have, for instance, that `A * A = A ^ 2`. This can be shown to apply even if `A :: Cat`.

In this context, `X, Y, Z :: FinSet`, `Z ^ (X * Y) = (Z ^ Y) ^ X` becomes a simple arithmetic rule. For instance,
`2 ^ (3 * 4) = (2 ^ 3) ^ 4` can be seen as a purely categorical statement.

## Adjoint Functors

If `A, B :: Cat`, we can define a functor `Exp : A * B -> A ^ B`. Let us fix `b :: B` in place. We can shorten this to
`(-) ^ b : A -> A ^ B`. Similarly, we can fix `b` in place in `Prod : A * B -> A * B` to get `(-) * b : A -> A * B`.
Looking at `hom(X * Y, Z) ~= hom(X, Z ^ Y)`, let us rewrite it as `hom(a * c, b) ~= hom(a, b ^ c)`. Using our newly
defined functors, the formula can be rewritten as `hom( ((-) * c) a, b) ~= hom(a, (- ^ c) b)`. Let us denote
`F = ((-) * c)`, `G = (- ^ c)`. Then we have `hom(F a, b) ~= hom(a, F b)`.

In other words, the functors `F`, `G`, when applied to the left, respectively to the right of the homfunctor's product
category domain, induce a natural bijection. Let us generalize this property to any pair of functors. In this
specific case, `F, G : [Cat, Cat]`, however, in general, `F` is some functor `F :: [C, D]`. In this case, the
homfunctor on the left must be `hom : (op D) * D -> Set`, as `F a :: D`, and the one on the right must be
`hom : (op C) * C -> Set`, as `a :: C`. This obliges `G :: [D, C]`, as `b :: D`, `F b :: C`.

In other words, for `F :: [C, D]`,  `G :: [D, C]`, `hom_D : (op D) * D -> Set`, `hom_C : (Op C) * C -> Set`, we have
`hom_D(F a, b) ~= hom_C(a, G b)`. Let us call the relation between `F` and `G` an adjunction, denoted `F -| G`.
`F` and `G` are called the adjoint functors, and we declare `F` as the left adjoint of `G`, and `G` as the
right adjoint to `F`. This is due to `F` being on the left side of the homfunctor's product category domain,
and `G` being on the right side.

## Adjoint Functors intuition

Intuitions on adjunctions can be derived from the formula `hom_D(F a, b) ~= hom_C(a, G b)`. Recall that `a :: C`,
`b :: D` are any values in their respective categories. As such, the adjoint functors have a relation that is both
symmetric and opposite: by applying `F` to some object `a` and then going to some other object `b`, you get the same
cardinality of morphisms as if you started at `a` and went to the application of `G` to `b`. 

This can be seen with the product-exponent adjunction, which acts as the archetypal adjunction. `(-) * b` and
`(-) ^ b` are not isomorphic, but they share some underlying structure. Applying a product to the left and then
drawing morphisms going out of it is like adding an argument to a function's domain. Applying an exponent to the
right and drawing morphisms going into it is like having a function return another function, which when applied to an
argument, returns a result. Notice that these are practically equivalent, which is why currying and uncurrying work.

Adjunctions, in the general case, encode a duality of functors. There are a lot of adjunctions, and any intuition
beyond that of a duality will not hold for all cases. However, because the left adjoint is on the left of the homset,
it will often embed objects in a category in a manner that has nice outbound morphisms to other objects. Meanwhile, the
right adjoint will often embed an object so that it can be reached nicely by inbound morphisms from other objects.