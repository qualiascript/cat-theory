# Chapter 4: Functor Categories

Is there a category of functors? If there is, it is an object in `Cat`, as it is a valid category. Morphisms in `Cat`
are exactly functors, so the existence of functor categories would imply the existence of an internal homfunctor over
`Cat` with the definition `hom : (op Cat) * Cat -> Cat`. This raises the question: what is a suitable definition for a
morphism in a functor category?

A functor category between `C, D :: Cat` will henceforth be denoted as either `[C, D]` or `D ^ C`, depending on which
notation is more clear in a specific context. As we will see later on, the notation `D ^ C` is equivalent to
exponentiation of sets when `D, C :: Set`, and even exponentiation of natural numbers when `D, C :: FinSet`. As such,
functor categories can also be referred to as exponential objects.

As the objects in `[C, D]` are all possible functors from `C` to `D`, a morphism ought to represent a composable
relation on functors. We have already established that functors are composable, as given `F :: [C, D]`, `G :: [D, E]`,
we have `F . G :: [C, E]`. But this composition, called horizontal composition, is between two functors in different
functor categories, unless `C = D`. Instead, we require a morphism between two functors `F, G :: [C, D]`, so that if we
have `alpha, beta :: [C, D] ^ I`, `alpha : F -> G`, `beta : G -> H`, we can obtain `alpha . beta : F -> H`. Let us call
morphisms of functor categories natural transformations.

## Natural transformations

Recall that functors are defined as being pairs of functions between the object sets and homsets of two categories.
In other words, if there are two functors `F, G :: [C, D]`, `F` sends some object `x` of `C` to some object `F x` of
`D`, and `G` sends it to a different object `G x` in the same category. The same applies to morphisms.

In order to fulfill the morphism composition, it seems natural to define a morphism between `F, G :: [C, D]` as
an operation that transforms all `F x` to `G x` for `x :: C`, and all `F f` to `G f` for `f :: C ^ I`. We will denote
the resulting natural transformation `alpha`, its transformation of `x` as `alpha_x` and its transformation of `f`
as `alpha_f`.

Given any `f :: C ^ I`, we need to establish what `alpha_f : F f -> G f`, does. Note that given `x :: C`,
`F x, G x :: D` so `alpha_x :: D ^ I`. Also note that if `f :: C ^ I`, `F f, G f :: D ^ I`. In other words,
`F f, G f, alpha_x, alpha_y :: D ^ I`.

For clarity, let us use the notation `x -- f -→ y` for`f : x -> y`. By chaining `x -- f -→ y -- g -→ z`, we demonstrate
that `f` and `g` are composable. Let us also allow this notation to trace 2D paths using `|` for the horizontal arrow
body, and allow the ending symbol to be `↓` instead of `→`.

Then, for any `f :: C ^ I`, `f : x -> y`, we have `F x :: D`. We can now trace the following path:
`F x -- F f -→ F y -- alpha_y -→ G y`. However, we also have `F x -- alpha_x -→ G x -- G f -→ G y`. These two 
trace the same path, which can be visualized as the following diagram:

```
   F x -- F f -→ F y
   |               |
   |               |
alpha_x         alpha_y
   |               |
   ↓               ↓
   G x -- G f -→ G y
```

Since we have a unique `alpha_f : F f -> G f` for any `f :: C ^ I`, `f : x -> y`, this can be envisioned as a
unique `f' :: (D * D) ^ I` from `(F x, F y)` to `(G x, G y)`. This implies the value of `G y` is uniquely determined
by `F x`. However, we have two methods of calculating it, namely `(F f) . alpha_y` and `alpha_x . (G f)`.
Thus, `(F f) . alpha_y = alpha_x . (G f)`, which is known as the naturality condition of natural transformations.

## Natural isomorphisms

As the functor category is a category, every `F :: [C, D]` has an identity morphism `id F :: [C, D] ^ I`, in other
words, an identity functor. As natural transformations are defined piecewise as a morphism `(id F)_x` for
`F x :: D`, and the mapping of morphisms `F f :: D ^ I` is fully determined by the mapping of objects to morphisms,
one can obtain an identity morphism for `F` by defining `(id F)_x = id (F x)`. Practically speaking, applying
the identity natural transformation to a functor has no action.

A composition between a functor and natural transformation can be defined using identity natural transformation.
For `X :: [C, D]`, `alpha :: [C, D] ^ I`, let's denote `X . alpha` as synonymous with `(id X) . alpha`, and
`alpha . X` as synonymous with `alpha . (id X)`.

If we have `F, G :: [C, D]`, `alpha, beta :: [C, D] ^ I`, `alpha : F -> G`, `beta : G -> F`, `alpha . beta = id F`,
`beta . alpha = id G`, then `alpha` is an isomorphism in `[C, D]`. The relation between `F` and `G` is denoted as a
natural isomorphism. 

## Natural transformation intuition

Natural transformations are named as such because they transform the nature of a functor into another functor in a
composable manner. Recall that functors act as morphisms in `Cat` that transform some category to another. Natural
transformations, then, are transformations of transformations. The naturality condition establishes that, given two
functors `F, G :: [C, D]` and a natural transformation `alpha : [C, D] ^ I`, we can safely perform operations using the
functor `F`, ignoring `G`. When we apply the natural transformation, it will have the same result as if we operated 
using `G` from the beginning. 

Consider if the category `D` is a more complex category, like `Cat`. In that case, one can have two functors,
`F :: [C, X]`, `F :: [C, Y]`, and if `X`, `Y` are subcategories of `Cat`, their domain can be widened to
`F, G :: [C, Cat]`, despite not using the entire codomain. In this case, one can define a natural transformation
`alpha :: [C, Cat] ^ I` between thw two despite the codomains seemingly not matching up. Practically speaking,
one can move around any `x :: C` through various categories without ever operating directly in `C`. This is the
principle underpinning generic programming.

## Example of a functor category

The arrow category of a category `C :: Cat` is the category whose objects are morphisms of `C`. It is denoted as
`C ^ I`, where `I` is the walking morphism. In other words, it's the category of functors from `I` to `C`. 
A `[I, C]` functor must select where each of the two objects of `I` are mapped, as well as its unique non-trivial
morphism. This is the same as picking a morphism of `C`, so the object of all functors `[I, C]` selects all morphisms.