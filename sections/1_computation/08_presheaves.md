# I.8. Presheaves

For any `C :: Cat`, we have an external homfunctor `hom : (op C) * C -> Set`. By currying (that is, the product
exponent adjunction), this induces a functor `Yo : C -> [op C, Set]`. This functor is known as the Yoneda embedding,
for reasons that will become apparent shortly. An object in the category of `[op C, Set]` is known as a presheaf.
It is a covariant functor, meaning for `Pr :: [op C, Set]`, `f, g :: C ^ I` composable morphisms, we have
`Pr(f . g) = Pr g . Pr f`.

The presheaves induced by the Yoneda embedding are given by `Yo c = hom(-, c)`, but in the general case, a presheaf
is simple a functorial mapping of each object of `C` (as they are the same as the objects of `op C`) to a set.
This induces a category of presheaves `[op C, Set]`, which is a functor category whose morphisms are natural
transformations. 

In general, a presheaf maps objects to sets. As such, it can be understood as a method of probing a category,
as to simplify the categorical objects to sets, which form the usual foundation of mathematics. As such, the category
of presheaves must encode all possible probes on a category, or in other words, everything there is to know about a
category which is expressible in sets. But the Yoneda embedding is bijective to the homfunctor, so if there are probes
that cannot be derived from it, then category theory cannot act as a general model for mathematical objects.

## Representable Presheaves

A presheaf which is the result of the application of the Yoneda embedding is called a representable presheaf. We would
like for any presheaf to be a natural transformation from some representable presheaf to some other presheaf. Let's
call the second presheaf `Pr :: [op C, Set]` for `C :: Cat`. Given the Yoneda embedding `Yo : C -> [op C, Set]`,
in order to obtain a representable presheaf, we must select an object `c :: C`. Then, let us look at natural
transformations between `Yo c` and `Pr`.

Natural transformations are morphisms between functors, and as such, we can use the external homfunctor to define the
set of natural transformations as `Hom_{[op C, Set]}(Yo c, Pr) :: Set`. We know that `Yo c = hom(-, c)`, so we get
`Hom(hom(-, c), Pr)`. We must check what the naturality condition does for a morphism `f :: C ^ I`, `f : x -> y`. If
we label our natural transformation `alpha :: [op C, Set] ^ I`, we get:

```
  Hom(x, c) -- Hom(f, c) -→ Hom(y, c)
  |                         |
  |                         |
alpha_x                   alpha_y
  |                         |
  ↓                         ↓
  Pr x ------- Pr f ------→ Pr y
```

Thus, `alpha_x . Pr f = Hom(f, c) . alpha_y`. However, we also know one element of `Hom(x, c)` which must exist: the
identity morphism of `c`, `id c`. The natural transformation then maps `id c` to some `u :: Pr c`. Meanwhile, for
some morphism `g : Hom(c, c) -> Hom(y, c)`, it will send `id c` to `id c . g = g`. Then, by applying the naturality
condition for the case of `id c`, we get `Pr g u = g . alpha_y`. 

But we have `g : Hom(c, c) -> Hom(y, c)`, which is equivalent to `g : c -> y`. Thus, for any `g`, `y`, we have that
the component of the natural transformation `alpha_y` at `g` is `Pr g u`, meaning it is determined by the selection
of `u :: Pr c`. Given some morphism `f : x -> y`, both the value of `alpha_x` and `alpha_y` is also determined by
`u`, and so is the mapping of the morphism.

In other words, there is a natural bijection `hom(Yo c, Pr) ~= Pr c`. This is known as the Yoneda Lemma.

## Yoneda Embedding

In particular, if we select `Pr = Yo d`, we get `hom(Yo c, Yo d) ~= Yo d c`, but `Yo d = hom(-, d)`, so we have
`hom(Yo c, Yo d) ~= hom(d, c)`, for any `c, d :: C`. This demonstrates that `Yo` is a natural isomorphism for
`op C`, or `Yo = op C`. Thus, `Yo` is referred to as a full and faithful functor. A full functor induces a surjective
function between homsets for any `c, d :: C`, and a faithful functor induces an injective function. As we have a
natural bijection, the Yoneda embedding induces both.

Let us consider a presheaf `Pr :: [op C, Set]` as an attempt to select the elements of every `c :: C`, in a suitable
sense for whatever the category represents. The representable presheafs are the most canonical representation of the
elements, insofar as any other presheaf is reducible to it. Then `hom(Yo c, Yo d) ~= hom(d, c)` represents the element
set of `c` from the perspective of `d`. But this is just the set of morphisms inbound to `c`. Thus, we get to an odd
conclusion: the morphisms inbound to an object can be thought of as their generalized elements.

## Yoneda Lemma intuition

The Yoneda lemma is `hom(Yo c, Pr) ~= Pr c`. Recall that `Pr :: [op C, Set]`. This means that given some `c :: C`,
the set elements that `Pr c` maps to are exactly encoded in natural transformations from the Yoneda embedding at `c`
to the presheaf. Thus, the Yoneda embedding truly encodes everything there is to know about category `C`: any probe
over `C` returns a set that is fully encoded in the natural transformations of `Yo`, which itself encodes everything
about `C`.

This demonstrates that categories don't have any hidden information which is not encoded in their homset but that an
external probe over its objects would reveal. Thus, one gets the informal description of the Yoneda lemma: objects
are determined by their morphisms. Or simply put: category theory works.

In philosophical terms, the Yoneda lemma provides a basis for the position of mathematical structuralism.
Structuralism asserts that mathematics is the study of morphisms, not of objects. Objects only exist insofar as they
are the origin and destination of morphisms. Category theory, as defined in this guide, still relies on the existence
of sets, but the category theory based Univalent foundations project is building a wholly structuralist approach
to the study of mathematics.