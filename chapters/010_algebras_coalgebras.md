# Algebras and Coalgebras

Informally speaking, an algebra is a set and some operations over that set that follow some laws. This concept makes
for a good candidate for categorification.

We may start by considering a category `C :: Cat` and some functors representing possible operations. For
instance, a binary operation could be given by `F :: [C * C, C]`. However, this would only work if all objects we
want to operate on are `c :: C`. Instead, we could consider each `c :: C` as a data type, and then an operation would
simply be a morphism `f :: C ^ I`, `f : c * c -> c`. In fact, a binary operation is always a morphism `c * c -> c`, for
all `c :: C`, so we could build an endofunctor `F :: [C, C]`, `F x = x * x`.

Then, we could consider an algebraic operation to be a morphism `a : F x -> x`. It would seem, then, that in order
to encode an algebra, we require a family of such morphisms. However, that is not the case: a unary and a binary
operation can be encoded as a single morphism using the functor `F x = x + x * x`. Then, due to the behavior of
coproducts, a morphism `a : F x -> x` is equivalent to two morphisms, `a1 : x -> x` and `a2 : x * x -> x`. An algebra
can also include specific given values, which can be added to the functor as `F x = 1 + x + x * x`.

This construction is called an algebra over an endofunctor, or an F-algebra. More specifically, the algebra is given
by the object `c :: C`, called a carrier, and the morphism `a : F c -> c`.

## Homomorphisms between Algebras

Let us then consider the category of F-algebras. All the information about the F-algebra is encoded in the morphism
`a : F c -> c`, so `a :: C ^ I`. However, this is too broad, as not all morphisms in `C` are algebras. We are operating
in a subcategory of `C ^ I`, which we can label `Alg`. We can use the fact that `Alg` is a subcategory of `C ^ I` by
observing that `C ^ I` is a functor category, and as such morphisms in `Alg` ought to be natural transformations. A
natural transformation between algebras is also known as a homomorphism.

A natural transformation from `F` to `G` involves mapping all objects and morphisms from `F f` to `G f`. However, in
this case, we have only one morphism in each functor's image. As such, for a natural transformation from `a : F c -> c`
to `b : F d -> d`, the components of the natural transformation are `f : c -> d` for the destination of the morphisms
and `F f : F c -> F d` for the origins. Practically speaking, a morphism in the category of F-algebras is completely
given by a morphism between the carriers of the F-algebra.

## Initial algebra

The initial object over `Alg`, if it exists, is referred to as an initial algebra. Let's assume that `a : F c -> c`
is an initial algebra over `F`. Then, `b : F F c -> F c` is also an algebra, so there is exactly one morphism
`f : c -> F c`. However, `a : F c -> c` is also a valid algebra homomorphism from `b` to `a`. Then, `f . a : c -> c`
constitutes a homomorphism from `a` to `a`. However, as `a` is initial, its only endomorphism is `id c`. Hence,
`f . a = id c`, meaning `f : c -> F c` is an isomorphism, so `c = F c`. This is known as Lambek's theorem.

In other words, if an initial algebra over `F` exists, it is `a : F c -> F c` where `a` is an isomorphism. For
instance, given `C, X :: Set`, `F C = 1 + X * C`, the initial algebra on `C` is `a : F C -> 1 + X * C`, so we
have that `C = 1 + X * C = 1 + X * (1 + X * C) = 1 + X * (1 + X * (1 + X * C))` etc. Consider what it would mean for
`l :: c`: at each coproduct, it must decide whether to pick `1` and terminate, or pick an `x :: X` to fill and
continue the recursion. This is the same as selecting a number of elements of `X`, so it can be denoted `List X`.

## Coalgebras

F-coalgebras are the dual concept to F-Algebras. Given a `F :: [C, C]`, an F-coalgebra comprises an object `c :: C`
and a morphism `c -> F c`. A terminal coalgebra, if it exists, is the terminal object in the category of coalgebras.
Similarly to F-Algebras, if it exists, the terminal coalgebra's value is given by `c = F c`.

Coalgebras can be thought of as an encoding of potentially infinite sequential operations. For instance, for functor
`F C = X + C * C`, there is no initial algebra, as the structure is necessarily infinite. However, as a terminal
coalgebra `a : C -> X + C * C`, one obtains `C = X + C * C = X + (X + C * C) + (X + C * C)` etc. which is an infinite
binary tree with leaves labeled some value `x :: X`. This works, as one would need to make infinite steps of unfolding
in order to reach the infinite structure.

## Monoids

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
