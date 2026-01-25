# Products and Exponents [WIP]

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
homsets of `Cat`. So for functor `hom : (op Cat) * Cat -> Cat`, we have a bijection between `hom(X * Y, Z) :: Set` and
`hom(X, Z ^ Y) :: Set`. In other words, `hom(X * Y, Z) = hom(X, Z ^ Y)`.

## Products and Exponents in `Set`

Recall that if `S :: Set`, `S` has no non-trivial morphisms. Thus, the product category of two sets is exactly
the Cartesian product. Since `Set` has an internal homfunctor, the exponentiation of two sets is also a set.
Specifically, it is a set of functions. Applying `hom(X * Y, Z) = hom(X, Z ^ Y)` in the context of sets, we get that
`Z ^ (X * Y)` and `(Z ^ Y) ^ X` have the same cardinality, which in `Set`, means they are isomorphic. In other words,
`X, Y, Z : Set`, `Z ^ (X * Y) = (Z ^ Y) ^ X`.

Since this applies in `Set`, it applies in its subcategory `FinSet` as well. recall that the objects of `FinSet` are
natural numbers. In this context, `X, Y, Z : FinSet`, `Z ^ (X * Y) = (Z ^ Y) ^ X` becomes a simple arithmetic rule.
So for instance, `2 ^ (3 * 4) = (2 ^ 3) ^ 4` can be seen as a purely categorical statement.

[TO BE CONTINUED]