# Chapter 4: Functor categories

Is there a category of functors? If there is, it is an object in `Cat`, as it is a valid category. Morphisms in `Cat`
are exactly functors, so the existence of functor categories would imply the existence of an internal homfunctor over
`Cat` with the definition `hom : (op Cat) * Cat -> Cat`. This raises the question: what is a suitable definition for a
morphism in a functor category?

A functor category between a category `C` and a category `D` will henceforth be denoted as either `[C, D]` or `D ^ C`,
depending on which notation is more clear in a specific context. As we will see later on, the notation `D ^ C`
is equivalent to exponentiation of sets when `D` and `C` are in `Set`, and even exponentiation of natural numbers when
`D` and `C` are in `FinSet`. As such, functor categories can also be referred to as exponential objects.

As the objects in `[C, D]` are all possible functors from `C` to `D`, a morphism ought to represent a composable
relation on functors. We have already established that functors are composable, as given `F : C -> D`, `G : D -> E`,
we have `F . G : C -> E`. But this composition, called horizontal composition, is between two functors in different
functor categories, unless `C = D`. Instead, we require a relation between two functors `F, G : C -> D`, so that if we
have two morphisms `F -> G` and `G -> H`, we can always obtain `F -> H`. Let us call this relation a natural
transformation.

## Natural transformations

Recall that functors are defined as being pairs of functions between the object sets and homsets of two categories.
In other words, if there are two functors `F, G : C -> D`, `F` sends some object `x` of `C` to some object `F x` of
`D`, and `G` sends it to a different object `G x` in the same category. The same applies to morphisms.

In order to fulfill the morphism composition, it seems natural to define a morphism between `F, G : C -> D` as
an operation that transforms all `F x` to `G x`, whether `x` is an object or a morphism in `C`. We will denote the
resulting natural transformation `alpha`. Piecewise, we will denote the transformation of some `F x`, where `x` is
either an object or morphism, into `G x`, as `alpha_x`.

Given any morphism `f`, we need to establish what `alpha_f : F f -> G f`, does. Note that, if `x` is an object,
`F x` and `G x` are both objects in `D`, meaning `alpha_x` is simply a morphism in `D`. Also note that if `f` is a
morphism in `C`, both `F f` and `G f` are also morphisms in `D`. In other words, all of `F f`, `G f`, `alpha_x` and
`alpha_y` are morphisms in D.

For clarity, let us use the notation `x -- f -→ y` for`f : x -> y`. By chaining `x -- f -→ y -- g -→ z`, we demonstrate
that `f` and `g` are composable. Let us also allow this notation to trace 2D paths using `|` for the horizontal arrow
body, and allow the ending symbol to be `↓` instead of `→`.

Then, for any morphism `f : x -> y` in `C`, we can obtain an object `F x` in `D`. We can now trace the following path:
`F x -- F f -→ F y -- alpha_y -→ G y`. However, we also have `F x -- alpha_x -→ G x -- G f -→ G y`. These two trace the
same path, which can be visualized as the following diagram:

```
   F x -- F f -→ F y
   |               |
   |               |
alpha_x         alpha_y
   |               |
   ↓               ↓
   G x -- G f -→ G y
```

Since we have a unique `alpha_f : F f -> G f` for any morphism `f : x -> y` of `C`, this can be envisioned as a
unique morphism in `D * D` from `(F x, F y)` to `(G x, G y)`. This implies the value of `G y` is uniquely determined by
`F x`. However, we have two methods of calculating it, namely `(F f) . alpha_y` and `alpha_x . (G f)`.
Thus, `(F f) . alpha_y = alpha_x . (G f)`, which is known as the naturality condition of natural transformations.

## Natural transformation intuition

[TO BE COMPLETED]
