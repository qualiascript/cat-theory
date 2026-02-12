# II. 5. Subobject Classifiers

In `Set`, every monomorphism `f : X -> Y`, considered as a subobject of `Y`, is equivalent to a morphism `f' : Y -> 2`,
mapping each element of `Y` to `1` if `f` includes it and `0` otherwise. In fact, if we define `true : 1 -> 2` selecting
the terminal object, we get that `X = Pb(f', true)`, so that the subobject consists of the elements of `Y` which map
to the terminal object. Note that in `Set`, the membership logic is two-valued, but this is not a requirement in all
categories we would like to model. As long as there is a canonical `true` morphism, the same construction can be used.

A subobject classifier is a morphism `true : 1 -> Om` with the property that for any monomorphism `f : X -> Y`, there
is a unique morphism `f' : Y -> Om` so that `X = Pb(f', true)`. `Om` is denoted the object of truth values. In fact,
consider the subobject assigning presheaf `Sub : Op C -> Set`, so that `Sub X` is the set of subobjects of `X`. It can
be shown that if `Sub` is representable, it is of form `Sub X = hom(X, Om)`, so that the representability of `Sub` 
implies there is a subject classifier `true : 1 -> Om`, whose selected object of `Om` is terminal in the category.

## Power Objects

A topos is finitely complete CCC which has a subobject classifier. In fact, it is also a Heyting category, which can
be derived from this definition. Let us go through the derivation. Consider subobjects of `X * Y`. If there is a
subobject classifier, they are given by `Sub(X * Y) = hom(X * Y, Om)`. If the category is a CCC, we can curry to
`Sub(X * Y) = hom(X, Om ^ Y)`. This is the collection of morphisms from `Y` to `Om`, or in other words, the collection
of subobjects of `Y`. As the set of subsets of a set is known as a power set, `Om ^ Y` is denoted a power object. 

Thus, in a Topos, any `Y` has a power object `Om ^ Y`, and a subobject of `X * Y` is a monomorphism `f : X -> Om ^ Y`.
In particular, a subobject of `Om ^ Y * Y` is a monomorphism `f : Om ^ Y -> Om ^ Y`. Let us take `f = id(Om ^ Y)`.
For any `y :: Y`, we get `f_y = id(Om ^ y)`, so that the subobject at `y` is `Pb(id(Om ^ Y), true)`, i.e., the
subobjects induced by `y` which are true. Then, overall, this induces a morphism `In : R -> Om ^ Y * Y`, consisting of
the elements of `Y` and the set of subobjects of `Y` which contain them. 

Then consider some other subobject `H : R -> Y * Z`. We know that `Sub(Y * Z) = hom(Z, Om ^ Y)`, so this induces
a unique morphism `H' : Z -> Om ^ Y`. We have that `H' = H' . id(Om ^ Y)`. For some `y :: Y`, `z :: Z`, the subobject
at these values is given by `Pb(H', true)`, which selects subobjects of `Y` that are at both `y` and `z`. This is
exactly a fiber product, defined in the internal language of a Topos. Furthermore, the `In` morphism has the property
that given any other `H : R -> Y * Z`, there is a unique `H'` so that `H` is the pullback of `H'` and `In`.

## Topos as Heyting Category

For our purposes, a simpler definition of a Heyting category is as a category where each object induces a Heyting
algebra, by taking its subobjects as posets. A Heyting algebra is a lattice where the product-exponent adjunction
holds, and a lattice is a poset with all meets and joins (finite products and coproducts). We seek to construct
the necessary structure in order to make our arbitrary Topos into a Heyting category. Specifically, we will construct
a functor `Sub : C -> HeytAlg`, which we have been already using implicitly.

Topoi are finitely cocomplete. While proving this is beyond the current scope, this can be seen as a consequence of the
following: `hom(A, Om ^ B) = hom(A * B, Om) = hom(B * A, Om) = hom(B, Om ^ A) = hom_{op C}(Om ^ A, B)`. Then, taking
`Om ^ (-) : Op C -> C` as a functor, it is left adjoint to itself in the opposite category. Left adjoints often
preserve colimits, and since `op C` has all finite colimits (as it is the opposite of a category with all finite
limits), it suggests any topoi is finitely cocomplete. In fact, coproducts are part of the internal language of a topoi.

We have that `Sub X = hom(X, Om)`. Given `A, B :: Sub X`, this induces two monomorphisms `A : A' -> X`, `B : B' -> X`.
This is a thin skeletal category by definition. Then, `Pb(A, B)` is the product in the lattice, and generalizing, this
induces all finite products, with the terminal object given by `id X`. Coproducts are given by the canonical map
`C : A + B -> X`, which selects the largest subobject both are subobjects of. Given zero terms, the coproduct is the
initial object, which is `0` or `FALSE`.

We must also define the morphisms of the Heyting algebra, as implication. Recall that, by the product exponent
adjunction, `(A AND B) -> C ~= A -> (C -> B)`. Then, `A -> B = A -> (B -> B) = (A AND B) -> B`. In other words,
implication is given by the equalizer of `A` and `A AND B`, as elements of `Sub X`, which is a special case of a
pullback and as such it is defined within the internal language of the topos. It can also be seen that the product
exponent adjunction holds within each lattice. Thus, it is a Heyting algebra, and the Topos is a Heyting category.

Note that the Heyting algebras can be envisioned as slice categories restricted to monomorphisms, and these slices
are CCC. As such, a similar argument as has been made for LCCCs can be made in order to demonstrate that a base change
functor, which is simply an object of the topos, admits both left and right adjoints. Hence, the topos has all
dependent products and dependent sums, corresponding to existential and universal quantifiers. Adding this property,
the topos is a sufficiently rich model of Intuitionistic Logic.

## Topos intuition

Topoi have many possible interpretations. For our current purposes, it can be seen as a category whose internal
structure is rich enough as to serve as a model of mathematics. While the law of excluded middle does not in general
hold, it holds in some topoi, and as such it can also serve as a model for classical logic. All the axioms of ZFC, 
excluding the axiom of choice, can be derived in this manner, and the axiom of choice can also be added by constructing
a so-called choice object. In these terms, all mainstream mathematics can be seen as living within the logic of a topos.

An example of a topos, in fact, the archetypal example, is `Set`. This guide relies on set theory for its foundations,
but this can be retroactively seen as merely using the internal language of `Set` as a topos[^1]. In fact, as all topoi
hold the same structure, sans for excluded middle and the axiom of choice, a statement about sets which does not rely
on these axioms holds in any topos, by simply replacing the word choices. By constructing a topos that is not `Set`,
one obtains a lot of mathematical theorems for free. Simply find a finitely complete CCC with a subobject classifier.

We have demonstrated the correspondence between mathematical logic, computer programs and the internal language of 
category theory. In fact, there is one more level: as the name "Topos" suggests, these objects relate to topology. The
subobject classifier is not limited to binary true or false values, and this provides the necessary structure for such
topological models. As such, a generalization of topoi known as (infinity,1)-topos provides the inner language of
Homotopy Type Theory, which unifies all four concepts under one framework.

[^1]: Equipped for all sets with a Grothendieck universe that contains it.