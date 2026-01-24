# Products and Exponents [WIP]

Recall the homfunctor `hom : (op C) * C -> Set`. We have previously claimed that one can "fix" either the first
or the second value in the product category in the domain and obtain a new functor. More generally, given a functor
`F :: [X * Y, Z]`, there is a functor `alpha :: [X, Arr [X * Y, Z]]`, so that we have a natural transformation
`(alpha x) :: Arr [X * Y, Z]` for each `x :: X`. This is a categorization of the idea of "fixing" `x :: X` in the
original functor.

We can define `(alpha x)` component-wise: for each object `(x', y) :: X * Y`, one obtains `F (x', y) :: Z`. Then, we
define `(alpha x)_x :: Arr Z`, `(alpha x)_x' : F (x', y) -> F (x, y)`. It can be checked that this fulfills the
naturality conditions.

Let's then denote `G :: [X, [X * Y, Z]]`, `G (x) (x', y) = F (x, y)`. As the value of `x' :: x` is unused, 
`G x :: [X * Y, Z]` can be shown to be naturally isomorphic to `H :: [Y, Z]`. As such, we can simplify the object
to `G :: [X, [Y, Z]]`. Then, we have a function that takes a functor `F :: [X * Y, Z]`, and obtains a functor
`G :: [X, [Y, Z]]`.

We can also build the inverse function. Given any `G :: [X, [Y, Z]]`, we can build the object `X * Y`, as well as
functors `first :: [X * Y, X]`, `first (x, y) = x`, `second :: [X * Y, Y]`, `second (x, y) = y`. Then for any
`z :: X * Y`, `G (first z) (second z) = Z`. This constitutes a functor `F :: [X * Y, Z]`.

Since we have an invertible function that maps any `F :: [X * Y, Z]` to `G :: [X, [Y, Z]]`. But recall that functor
categories are equivalent to internal homsets of `Cat`. So for functor `hom : (op Cat) * Cat -> Cat`, we have a
bijection between `hom(X * Y, Z) :: Set` and `hom(X, Z ^ Y) :: Set`. In other words, `hom(X * Y, Z) = hom(X, Z ^ Y)`.