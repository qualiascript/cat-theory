# Part 1: Categories

## Definition
A category is a set[^1] of objects, paired with a set of morphisms from some object `A` to some object `B`. It can be
envisioned as a type of directed multigraph (although not every directed multigraph makes for a valid category), with
the objects acting as nodes and morphisms as edges. Additionally, a category must respect the following laws:
- If there exists a morphism `f` from `A` to `B` (henceforth denoted `f : A -> B`), and `g : B -> C`,
there also exists a morphism `f . g` (also denoted as `g ∘ f`) from `A` to `C`. This is morphism composition.
- For any object `X` in a category `C`, there is always (at least) one morphism from `X` to itself, denoted as `id X`. 
Composing with `id` morphisms does not change the result. That is, given `f : X -> Y`, `g : Y -> X`, we have
`(id X) . f = f`, `g . (id X) = g`.
- Morphism composition is associative. That is, `(f . g) . h = f . (g . h)` if the domains and codomains
of `f`, `g`, `h` match up to make composition possible.

## What are the objects and morphisms?

A category is anything that can be modeled as a category, by the definition given above.
Morphisms can be thought of as any sort of relation which is composable.
Objects can be thought of as the origin and destination of morphisms.
This is intentionally a very generic definition.
It is useful to think of it as more akin to an interface that a structure must implement in order to be classified
as a category, rather than a definition in the traditional sense.

## What is the intuition behind this definition?

The most essential category is `Set`. It is a category where the objects are sets, and the morphisms are functions.
It can be easily checked that for any set `S`, there is an id function `id S`, which maps each element to itself.
It can also be easily checked that for any two functions `f : A -> B`, `g : B -> C`, there is a composite function
`f . g`, that maps any `x` in `A` to the result of `g(f(x))`. Associativity and composition with `id` also apply.

In fact, `Set` can be seen as the archetypal category. Any mathematical object can be modeled as a set,
but within `Set`, any function that can be defined is a valid morphism. Other categories can have a more restrictive
definition of what counts as a morphism, due to there being "inner structure" that the morphisms must respect.

For instance, `(N, <=)`, the set of natural numbers with the less than or equal to operator, is also a category.
Its objects are the natural numbers, and there is one morphism between `A` and `B` if and only if `A <= B`.
It can be easily checked that there is always an identity morphism, as `A <= A` for any A,
as well as that if `A <= B` and `B <= C`, then `A <= C`.

Every natural number is defined in ZFC, the standard foundation of mathematics, as `x = {0, 1, ..., x-1}`, so the
elements of this category can also be conceptualized as sets, but in `Set`, there is a function from `2` to `1`,
namely `{0 : 0, 1 : 0}`. However, in our new category (which is a preorder), that is not a valid morphism.
This illustrates the sense in which category theory acts as a broad generalization of set theory.

## Isomorphisms

An isomorphism is a morphism `f` between two objects `A` and `B`, such that there is also a
morphism `g` between `B` and `A`, so that `g . f = id A` and `f . g = id B`. `g` is the inverse morphism of `f`.

This means that for any object `X`, if there is a morphism `X -> A`, it can be composed with f on the right 
(i.e., `X -> A . f`) to get a morphism `X -> B`, and the other way around. The same can be shown for`A -> X` and
`B -> X`, by precomposing (composing on the left) with `g` and `f` respectively. Furthermore, since
`A -> B -> A = id A`, `X -> A = (X -> A -> B) -> A = X -> B -> A`, shows that given `X -> B`, one can reconstruct
`X -> A`, and by analogy for the other three cases, all morphism pairs are recoverable from one to another.

In other words, the morphisms going into and out of `A` and `B` have a one-to-one equivalence. Or simply put, any
statement about `A` within a category also applies to `B`. So, in practice, the two objects can be used interchangeably.

## Other categories

`FinSet` is the category of finite sets. Within `FinSet` (as well as within `Set`), if two objects (i.e. sets) have the
same number of elements, they are isomorphic. This is because there is a bijective function between the two, which maps
each element from `A` to a different element from `B` (is injective) and reaches all elements in `B` (is surjective).
So the inverse function can be easily defined by inverting the domain and codomain, and composing the two returns a
constant function, which is what `id` is within `FinSet` (as a subcategory of `Set`).

As such, any set with `n` elements is isomorphic to the set `n`. So, without any loss of accuracy, we can simply state
that the objects of `FinSet` are the natural numbers, `0`, `1`, `2`, etc.

Another way of defining a category is by specifying its underlying directed multigraph. As such, we can define the
following family of categories:
- The empty category `0`, with no objects and no morphisms
- The singleton category `1`, with one object and no non-trivial (i.e. non-`id`) morphisms
- The dual category `2`, with two objects and no non-trivial morphisms
- Etc.

These categories can be safely denoted using the natural numbers. This is because, as they have no non-trivial
morphisms, they can be defined solely by their set of objects, and as we've seen, within `FinSet`, any set with
`n` values is isomorphic to `n`. Intuitively, the number `2` is an abstract representation of the existence of exactly
two objects of some type, which the categorical definition illustrates.

[^1]: Technically, it is only a set for so-called small categories, otherwise it is a class. However, due to Grothendieck universes, one can usually assume it to be a set