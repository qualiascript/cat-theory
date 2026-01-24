# Chapter 3: Homfunctors

We have defined the homset of a category as the set of morphisms. This terminology comes from a shortening of
"homomorphism set", where homomorphism acts as a synonym of morphism within the context of category theory.

For some `a :: C`, we can obtain a subset of the homset in two different ways: by picking the elements of the homset
where `a` is on the right side of the pair, or elements where `a` is on the left. In other words, the set of outbound
morphisms starting in `a`, and the set of inbound morphisms ending in `a`. But recall that, for some `C :: Cat`, the 
category `op C` inverts all morphisms. In other words, we can think of the operation of obtaining the set of inbound 
morphisms of `a` as equal to obtaining the outbound morphisms of `a` when `a :: op C`.

## Homfunctors

Observe that we then have a mapping from some `C` to `Set`. It is natural to ask whether this mapping forms a functor.
If it does, its definition is `hom(a, -) : C -> Set`, where `a :: C`. When applied to some `b :: C`,
`hom(a, -)(b) = hom(a, b)`, which is a set.

When applied to some `f :: C`, `f : x -> y`, we ought to obtain a function `hom(a, f) :: Arr Set` between
`hom(a, x)` and `hom(a, y)`. Recall that the elements of `hom(a, x)` are morphisms from `a` to `x`. As such, this
function maps every morphism `g` of `hom(a, x)` to a morphism in `hom(a, y)`. This is equivalent to the morphism
composition `g . f`.

In order for this mapping to be a valid functor, for `f, g :: Arr C`, `f : x -> y`, `g : y -> z`, we must have
`hom(a, f . g) = hom(a, f) . hom(a, g)`. Notice that `hom(a, f) : hom(a, x) -> hom(a, y)` and
`hom(a, g) : hom(a, y) -> hom(a, z)`, so `hom(a, f) . hom(a, g) : hom(a, x) -> hom(a, z)`, which has the same domain
and codomain as `hom(a , f . g)`. As such, composition is respected.

There is also a functor `hom(-, a) : op C -> Set`, which can be obtained easily by using the opposite category of `C`.
For some `C :: Cat`, a functor `f : op C -> D` is known as a contravariant functor. A regular functor can also be
denoted as a covariant functor.

In the most general sense, `hom` can be envisioned as a functor `hom : (op C) * C -> Set`. The object `a` can be fixed
into place on the left, resulting in `hom(a, -) : C -> Set`, or on the right, resulting in `hom(-, a) : op C -> Set`.
This is because, given a functor `F : A * B -> C`, one can set the value of `A` to be a constant object `a` of `A` and
obtain `F : B -> C`. Furthermore, `A * B` is isomorphic to `B * A`, so one can also obtain `F : A -> C`. This is
equivalent to currying, and the argument will be made more rigorous later.

## Internal homfunctors

For some category `C`, an internal homfunctor, if it exists is a homfunctor with the definition `hom : (op C) * C -> C`.
In other words, the result of the homfunctor is also an object in `C`, hence it being called internal. It can be
trivially seen that `Set` has an internal homfunctor, as the result of applying the generic homfunctor to some set `a`
is a set, and applying it to some function `f` returns a function, which is a morphism in set.

## Homfunctor intuition

[TO BE COMPLETED]

