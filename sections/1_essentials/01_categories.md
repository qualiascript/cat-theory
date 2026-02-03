# I.1. Categories

## Definition

A category is a set[^1] of objects paired with a set of morphisms (named a homset). There are no limitations to what
the object set can entail. The homset can be envisioned as a set of triple pairs `(x, y, f)`, where `x`, `y` are values
of some category `C`'s object set (henceforth denoted `x, y :: C`) and `f` is a morphism which starts at object `x` and
ends at object `y` (henceforth denoted `f : x -> y`).

A category can be envisioned as a directed multigraph, with the objects acting as nodes and morphisms as edges.
However, compared to a directed multigraph, a category must additionally respect the following laws:
- If there exists a morphism `f: A -> B` and a morphism `g : B -> C` there also exists a morphism `f . g : A -> C`
(also denoted as `g ∘ f`). This is morphism composition.
- For any object `X :: C`, there is always a morphism `id X : X -> X`. There may be other morphisms `f : X -> X`
distinct from `id X` as well.
- Composing with `id` morphisms does not change the result. That is, given `f`, `g` morphisms of some `C` (henceforth
denoted as `f, g :: C ^ I`), if `f : X -> Y`, `g : Y -> X`, we have `(id X) . f = f`, `g . (id X) = g`.
- Morphism composition is associative. That is, for `f, g, h :: C ^ I`, `f : A -> B`. `g: B -> C`, `h : C -> D`,
we have `(f . g) . h = f . (g . h)`.

## Objects and morphisms

A category is anything that can be modeled as a category, by the definition given above.
Morphisms can be thought of as any sort of relation which is composable.
Objects can be thought of as the origin and destination of morphisms.
This is intentionally a very generic definition.
It is useful to think of it as more akin to an interface that a structure must implement in order to be classified
as a category, rather than a definition in the traditional sense.

## Category intuition

The most essential category is `Set`. It is a category where the objects are sets, and the morphisms are functions.
It can be easily checked that for any set `S :: Set`, there is an `id S :: Set^I`, which maps each element to
itself. Additionally, for any `f, g :: Set^I`, `f : A -> B`, `g : B -> C`, there is a `f . g : A -> C`, that maps any
`x :: A` to `g(f(x)) :: C`, here `f`, `g` taken as functions. Associativity and composition with `id` also apply.

In fact, `Set` can be seen as the archetypal category. Any mathematical object can be modeled as a set,
but within `Set`, any function that can be defined is a valid morphism. Other categories can have a more restrictive
definition of what counts as a morphism, due to there being "inner structure" that the morphisms must respect.

For instance, `(N, <=)`, the set of natural numbers with the less than or equal to operator, is also a category.
Its objects are the natural numbers, and there is one morphism between `A` and `B` if and only if `A <= B`.
It can be easily checked that there is always an identity morphism, as `A <= A` for any A,
as well as that if `A <= B` and `B <= C`, then `A <= C`.

Every natural number is defined in ZFC, the standard foundation of mathematics, as `x = {0, 1, ..., x-1}`, so the
elements of this category can also be conceptualized as sets, and there is a `f :: Set^I`, `f : 2 -> 1`,
namely `{0 : 0, 1 : 0}`. However, in our new category (which is a preorder), that is not a valid morphism.
This illustrates the sense in which category theory acts as a broad generalization of set theory.

## Isomorphisms

An isomorphism is a morphism `f :: C ^ I` `f : A -> B`, such that there is a `g :: C ^ I`, `g : B -> A`
so that `f . g = id A` and `g . f = id B`. `g` is the inverse morphism of `f`.

This means that for any `X :: C`, if there is a morphism `h :: C ^ I`, `h : X -> A`, it can be composed with f on the
right, i.e. `h . f : X -> B`. Same argument for `h' :: C ^ I`, `h' : X -> B`. Then, for `j, j' :: C ^ I`, `j : A -> X`,
`j' : B -> X`, one can obtain `g . j : B -> X`, `f . j' -> A : X` by precomposing, i.e., composing on the left. As such,
all morphisms coming inbound towards `A` or outbound from `A` also induce a morphism with `B` and vice versa.

Furthermore, since `f . g = id A`, `h : X -> A` induces `h = h . (f . g) = (h . f) . g = h' . g`, so `h = h' . g`,
and similarly, `h' = h . f`. By analogy, `j = f . j'`, `j' = g . j`. In other words, the morphisms going into and out of
`A` and `B` have a one-to-one equivalence. Or simply put, any statement about `A` within a category also applies to `B`.
So, in practice, the two objects can be used interchangeably.

## Other categories

For any two categories, `A` and `B`, there is a product category `A * B`. This is obtained by simply applying the
Cartesian product operation to the underlying object sets and morphism sets of the two categories. Its elements
are pairs of elements `(a, b)`, where `a :: A`, `b :: B`. Its morphisms are`(f, g) : (x1, x2) -> (y1, y2)`.
Products will be explored in more detail later on.

`FinSet` is the category of finite sets. If `A, B :: FinSet` have the same number of elements (i.e. cardinality),
they are isomorphic. This is because there is a bijective function between the two, which maps each element from `A` to
a different element from `B` (is injective) and reaches all elements in `B`(is surjective). So the inverse function can
be easily defined by inverting the domain and codomain, and composing the two returns a constant function, which is what
`id` is within `FinSet` (as a subcategory of `Set`).

As such, any set with `n` elements is isomorphic to the set `n`. So, without any loss of accuracy, we can simply state
that the objects of `FinSet` are the natural numbers, `0`, `1`, `2`, etc.

Another way of defining a category is by specifying its underlying directed multigraph. As such, we can define the
following family of categories:
- The empty category `0`, with no objects and no morphisms
- The singleton category `1`, with exactly one object and no non-trivial (i.e. non-`id`) morphisms
- The dual category `2`, with exactly two objects and no non-trivial morphisms
- Etc.

These categories can be safely denoted using the natural numbers. This is because, as they have no non-trivial
morphisms, they can be defined solely by their set of objects, and as we've seen, for `n :: FinSet`, any set with
`n` values is isomorphic to `n`. Intuitively, the number `2` is an abstract representation of the existence of exactly
two objects of some type, which the categorical definition illustrates.

Let us also define the category `I`. It is a category with exactly two objects, `A, B :: I`, and exactly one non-trivial
morphism `f : A -> B`. This category is called the walking morphism, and `C ^ I` is a category representing all
morphisms of `C`, for reasons that will be explained in due time.

[^1]: Technically, it is only a set for so-called small categories, otherwise it is a class. However, due to Grothendieck universes, one can usually assume it to be a set