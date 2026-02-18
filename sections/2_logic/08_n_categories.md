## II.8. n-Categories

So far, we have largely conflated isomorphism with equality, for instance by treating categories as their skeletal
version (induced by equivalence classes on isomorphisms). As a reminder, for morphisms `f, g, h :: C ^ I`, if we have
that `f . g = h`, this is an equality: morphisms are elements of the homest, which is in fact a set. By comparison,
concepts such as the terminal object being unique are "up to isomorphism": if there is another terminal object, it is
isomorphic to the one we identified, and can be used interchangeably. This is an awkward but important distinction.

Informally, consider `X` as some sort of topological space, whose objects are points and morphisms are continuous paths
between points. Given two paths, one can continuously deform one into the other, which is known as a homotopy. However,
categorically, a homotopy would be a morphism in the category of the internal homset. This is well-defined in `Cat`
as a natural transformation, but `X` is not `Cat`. In fact, a category with morphisms between morphisms is known as a
2-Category, with `Cat` being the archetypal example. The homotopy example illustrates the motivation for this concept.

Then, a 2-category is defined by objects, morphisms and 2-morphisms (i.e. morphisms between morphisms), subject to the
associativity and unit (identity) laws of regular categories. Note, however, that 2-morphisms can be composed in two
different ways: two natural transformations `a, b : [C, D] ^ I` can simply be applied successively in the functor
category, which is known as vertical composition. Alternatively, `x : [C, D] ^ I`, `y : [D, E] ^ I` can be horizontally
composed to yield `z : [C, E] ^ I`, by composing them on each side of `F . G` for functors `F : C -> D`, `G : D -> E`.

Let us denote `a * b` horizontal composition and `a . b` vertical composition for 2-morphisms. Then, we have the
following identity, known as the exchange law: `(a * b) . (c * d) = (a . c) * (b . d)`. This is, in fact, an equality,
not merely an isomorphism: natural transformations in `Cat` can be defined set-theoretically component-wise. However,
this is too strict for many relations we seek to model with 2-categories, and in fact, so are the associativity and
unit laws. Instead of strict equalities, these could be mere isomorphisms. In this case, they are known as bicategories.

In fact, in a bicategory, we have associator and unitor 2-isomorphisms that respect the correct coherence conditions.
In alternative terms, the objects are referred to as 0-cells, the 1-morphisms as 1-cells and the 2-morphisms as 2-cells.
Consider the case of a bicategory with one 0-cell: by treating its 1-cells as objects and 2-cells as morphisms, any
two 2-cells can be vertically composed in a manner respecting associativity and identity up to isomorphism. This is
precisely a monoidal category. This suggests a connection between higher categories and categories with extra structure.

## Delooping

2-categories have regular categories, which we will refer to as 1-categories, as their morphisms. Going further,
3-categories have 2-categories as morphisms, and in general, n-categories have `(n-1)`-categories as morphisms. They
also have equivalent laxer bicategories, tricategories etc. by imposing mere isomorphisms, not strict equality. We refer
to higher categories imposing equality as strict. In fact, lax categories induce strict ones by equivalence classes. By
extension, 0-categories are sets, as they are the collection type which morphisms of 1-categories inhabit. 

Then, we have that monoids are 1-categories with one object, and monoidal categories are 2-categories with one object
at the first level. Let us denote monoids as `(0,1)`-categories and monoidal categories as `(1,1)`-categories, and, in
general, let a `(n, k)`-category be a `(n + k)`-category which has one object at the first `k` levels. Alternatively,
this can be phrased as a `(k-1)`-connected `(n+k)`-category, where a `j`-connected category is one where all
`l`-cells for `l < j` are equivalent (i.e. either isomorphic or equal depending on strictness).

Consider a `(0,2)`-category. It is given by a 2-category whose 1-cell is a monoid. In fact, it is a monoid in two
different ways: by horizontal and vertical composition. The two monoids have the same identity, which we will denote
`1`. By the exchange law, `a . b = (a * 1) . (1 * b) = (a . 1) * (1 . b) = a * b`, so in fact the two monoids are
equivalent. Let us denote `a b = a . b = a * b`. Then, `a b = (1 a) (b 1) = (1 b) (a 1) = b a`. In other words, we
have that a `(0, 2)`-category is a commutative monoid. This is known as the Eckmann-Hilton argument.

The process of forming `(n, k)`-categories from `(k-1)`-connected `n+k`-categories is known as delooping. A related
result is known as the stabilization hypothesis. It states that if `k >= n + 2`, a `(n, k)`-category is equivalent to
a `(n, n + 2)`-category. Despite the name, this is in fact proven if delooping is well-behaved. A `(n, k)`-category is
also referred to as a `k`-tuply monoidal `n`-category. Intuitively, a `(n, 1)`-category is monoidal, and going upwards
in `k`-tupledness induces higher levels of commutativity, which when `n > 0`, is not a binary property.

## n-Groupoids

A Groupoid is a category where all morphisms are isomorphisms, taken non-skeletally. It is a generalization of groups,
insofar as a group is a groupoid with one object. A morphism being an isomorphism means it is invertible, which is the
property that defines groups. More broadly, an n-Groupoid is an n-Category where all `k`-cells for `k > 0` are
invertible. 0-categories only have identity morphisms, which are their own inverse, so all 0-categoies are 0-groupoids.
`n`-Categories have as their morphisms `(n-1)`-categories, so there are always `n`-categories of `(n-1)`-groupoids.

A 1-category of 0-groupoids is any 1-category. A somewhat odd question is what the 0-category of `(-1)`-groupoids
entails. In fact, sets form a poset by inclusion, given by the morphisms the subobject classifier maps to `1`. By
extension, a morphism between sets is a truth value, either binary or multivalued in the case of sheaves. Thus, the
`(-1)`-groupoid is the set of truth values. By extension, a `(-2)`-groupoid are morphisms on truth values, where `1`
is terminal. Thus, a `(-2)`-groupoid is the value `1`, or alternatively `TRUE`. It is also known as the point.

## Pointed n-Categories

Going back to `(n, k)`-categories, a `(n, 0)`-category is an `n`-category which is `(-1)`-connected, so that all
`(-1)`-cells are equivalent. We do not have a concept for a `(-1)`-cell, however, by extension, its morphisms ought to
be 0-cells, and it must have at least one such morphism, the identity morphism. Then, by slight abuse of notation,
we say that a `(-1)`-connected n-category is one that is inhabited. Thus, a `(n, 0)`-category is an inhabited
n-category. Alternatively, it is a pointed n-category, as in, an n-category `C` with a morphism `p : 1 -> C`.

## Higher Categories

It is, in general, difficult to study `n`-categories for `n > 2` directly. There are multiple competing notions of
laxness and strictness and an increasing number of possible compositions, beyond just horizontal and vertical. However,
there is an alternative in order to study higher category theory: find a suitable notion for infinity-categories and
use the generalization to talk of n-categories of desired strictness levels. This is the approach taken by Homotopy
Type Theory, which we will proceed in building the foundations of.