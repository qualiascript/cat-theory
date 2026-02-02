# Chapter 3: Homfunctors

We have defined the homset of a category as the set of morphisms. This terminology comes from a shortening of
"homomorphism set", where homomorphism acts as a synonym of morphism within the context of category theory.

For some `a :: C`, we can obtain a subset of the homset in two different ways: by picking the elements of the homset
where `a` is on the right side of the pair, or elements where `a` is on the left. In other words, the set of outbound
morphisms starting in `a`, and the set of inbound morphisms ending in `a`. But recall that, for some `C :: Cat`, the 
category `op C` inverts all morphisms. In other words, we can think of the operation of obtaining the set of inbound 
morphisms of `a` as equal to obtaining the outbound morphisms of `a` when `a :: op C`.

Once we have the set of all morphisms that start in `a`, we may also create a set of sets, where each element is some
`b` that is the destination of the morphism. Observe that, by setting `a` as a fixed value, we obtain a mapping from
the objects of `C` to `Set`. If we can also realize a suitable definition for the mapping of morphisms, we can create
a functor whose definition is `hom(a, -) : C -> Set`, where `a :: C`. When applied to some `b :: C`,
`hom(a, -)(b) = hom(a, b)`, which is a set.

## Homfunctors

The homfunctor, when applied to some `f :: C`, `f : x -> y`,  ought to obtain a function `hom(a, f) :: Set ^ I` between
`hom(a, x)` and `hom(a, y)`. Recall that the elements of `hom(a, x)` are morphisms from `a` to `x`. As such, this
function maps every morphism `m :: hom(a, x)` to a morphism in `hom(a, y)`. This is equivalent to the morphism
composition `m . f`.

In order for this mapping to be a valid functor, for `f, g :: C ^ I`, `f : x -> y`, `g : y -> z`, we must have
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
In other words, the result of the homfunctor is also an object in `C`, hence it being called internal. A category that
has an internal homfunctor is called a closed category. It can be trivially seen that `Set` is closed, as the result of
applying the generic homfunctor to some set `a` is a set, and applying it to some function `f` returns a function,
which is a morphism in set.

## Homfunctor intuition

Envisioning `C : Cat` as a multigraph with extra structure, and setting some `a :: C`, `hom(a, -) : C -> Set` is a
functor that, for some `b :: C`, returns the set of morphisms `f : C ^ I` with `f: a -> b`. This puts the focus on the
morphism structure of the category, rather than its objects. It allows one to probe what morphisms start in `a` and
end in another object, or, for the contravariant version, start in some object and end in `a`.

For `C :: Cat`, `hom : (op C) * C -> Set`, in fact, encodes all there is to know about a category. This can sound odd
at first, because the underlying objects and morphisms have values that are not encoded by the directed multigraph
structure. However, suppose you had another category `C :: Cat`, with a bijection between the object sets and homsets
so that if `x :: C` goes to `x' :: C'` and `y :: C` goes to `y :: C'`, then morphism `(x, y, f)` is sent by the homset
to value `(x', y', f')`. In this case one can define two functors, `F : C -> C'`, `F' : C -> C`, so that
`F . F' = id C` and `F' . F = id C'`. Then, `F :: Cat ^  I` is an isomorphism, so `C` and `C'` are isomorphic.

One may still wonder whether `C` and `C'` truly are equivalent in every way, or whether the categorical perspective
generates an isomorphism between two categories that encode different information in reality. In reality, `C` and
`C'` truly are the same mathematical object, which will be rigorously established later on. In fact, the underlying
values of the objects and morphisms of a category can be safely ignored: the underlying directed multigraph structure 
*is* the category, up to isomorphism. The category's homfunctor is merely another perspective on the same object.