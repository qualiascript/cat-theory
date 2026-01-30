# Monoids

A monoid is an F-algebra `a : 1 + X * X -> X`, meaning it has an element `i : X` and an operation `m : X * X -> X`,
which respect the laws that `m(m(x, y), z) = m(x, m(y, z))` (associativity) and `m(i, x) = m(x, i) = x` (left and right
identity). It is an important algebra in category theory. An example of a monoid can be constructed by setting
`X = FinSet`, `i = 0`, `m : (a, b) -> a + b`. This is the monoid of natural numbers with addition, and it can be
trivially checked to respect the monoid laws.

Notice that the associativity and the identity laws are respected by morphism composition. This suggests another monoid
construction, for some `M :: C`, set `X = hom(C, C)` in `a : 1 + X * X -> X`, alongside `i = id M`, `m(x, y) = x . y`.
In other words, a monoid can be constructed from the set of endomorphisms of any object in a category, along with
morphism composition. Since it is any category, we can also set `M :: Cat`. This demonstrates the set of endofunctors
of a category, along with functor composition, also constitute a monoid.

A monoidal category is given by an F-algebra `a : 1 + C * C -> C`, where `C :: Cat`, so that we have operations
`i :: C`, `m : C * C -> C` that respect the laws `m(m(x, y), z) = m(x, m(y, z))` and `m(i, x) = m(x, i) = x`.
An example of a monoidal category is given by the category of endofunctors `[D, D]`, with `i = id D` the identity
endofunctor, and `m(F, G) = F . G` functor composition.