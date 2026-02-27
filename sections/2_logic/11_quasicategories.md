# II. 11. Quasicategories

We have found that Kan complexes serve as a model for the fundamental `inf`-groupoids of homotopies. However, in
general, topological spaces can have continuous maps between them that are not invertible. When modeling such spaces,
it is only `k`-morphisms for `k > 1` that are invertible. Alternatively, from a categorical perspective, if we had
a model for `(inf, 1)`-categories, we could obtain `(inf, n)`-categories, and by allowing higher levels to be trivial,
`(m, n)`-categories for any `m` and finite `n`. As such, we seek to construct a `(inf, 1)`-category model.

Looking at Kan complexes, `H 2 0` and `H 2 2` model morphism inversion, meanwhile `H 2 1` models composition. For
higher levels, some horns correspond to morphism composition, and by taking the horn whose face is the origin face
in the morphism composition, this induces a morphism inversion. Then, let us define a quasicategory as a Kan complex
where all inner horns, that is horns `H n k` for `0 < k < n`, have fillers. This allows only morphism composition on
`1`-morphisms, but both composition and invertibility for `k`-morphisms where `k > 1`.

We defined `KanCplx` as a category where morphisms are equivalences of Kan complexes. Alternatively, we can define
`InfGrpd` to be the category of `inf`-groupoids where morphisms are continuous maps between the underlying topologies.
`InfGrpd` is an `(inf, 1)`-category that, regarded as a `1`-category, is isomorphic to `SSet`, and as such it forms
a `1`-topos (in fact an `(inf, 1)`-topos, as will become clear later). One of its subcategories is isomorphic to
`Set`, thus, from now on, let us treat `Set` in this manner, superseding the set theoretic foundations of this guide.

## Size Issues

Category theory is done on sets, but sets are objects of `Set`, which is a topos. As such, we can replace the
underlying sets with `inf`-groupoids and largely retain the same categorical semantics. However, we ought to deal with
size issues: by the Lawvere fixed point theorem, there is no set of all sets, and no `inf`-groupoid of all
`inf`-groupoids. We have avoided this issue by pointing to Grothendieck universes, and there is a similar construction
in topoi, known simply as universes. We refer to the objects of a universe as small, as compared to the universe.

Given a topos `T`, a universe is a morphism `el : E -> U`, so that a morphism `a : A -> I` is small if and only if
there is a morphism `f : I -> U` so that `a`, `f` and `el` form a pullback. Furthermore, we have the following axioms:
all monomorphisms into small objects are small, all small morphism compositions are small, the subobject classifier is
small and all small dependent products are small. Then, add the following axiom: all objects of a topos are small
relative to some universe. In `Set`, the universe containing the natural numbers set contains all provable ZFC sets.

The dependent product requirement, in particular, implies all power objects from small objects are small. This is
sufficient so that there is always a universe whose objects are all constructible objects, had there been no universes.
This is the sense in which we talk about "the category of all sets", which more formally is a category of all small
sets relative to a universe. As there is always a universe for an object, any set is an object of some `Set` category,
and this extends to all topoi. This sidesteps the paradoxes inherent to constructing categories that are "too large".

## Enrichment

Then, given a category, one can enrich it by replacing its underlying sets with `inf`-groupoids. For instance, a
`(n, 1)`-category is simply an `1`-category enriched on `inf`-groupoids. A presheaf out of an `(n, 1)`-category is a
functor `Pr : op C -> InfGrpd`. Then, the category of presheaves `[op C, InfGrpd]`, assuming everything is small, is an
`(inf, 1)`-topos. Clearly, so would be a category of `(inf, 1)`-sheaves, given an `(inf, 1)`-site. In general, the
logic of category theory is largely simply applicable to `(inf, 1)`-categories as well.

By similar logic, some simplicial sets correspond to quasicategories. An `(inf, 1)`-category enriched on simplicial
sets corresponding to quasicategories is an `(inf, 2)`-category. One example is given by the `(inf, 2)`-category of
`(inf, 1)`-categories, `(inf, 1)Cat`. Clearly, this process can be repeated as to yield `(inf, n)`-categories for any
finite `n`. By extension, one can also define `(m, n)`-categories, where all `k`-morphisms for `k > m` are trivial.
In particular, `(n, n)`-categories are simply `n`-categories, which we now have a concrete definition for.

## `inf`-topoi

`InfGrpd` is an `(inf, 1)`-category, so that its category of presheaves, `[op InfGrpd, InfGrpd]` is an `(inf, 1)`-topos.
One particular covering family is given, for each `o :: InfGrpd`, by the maximal and empty sieves. This reduces the
subobject classifier to simply `TRUE` and `FALSE`, so that its objects are simply subobjects of `InfGrpd` objects.
But `InfGrpd` already contains all such objects, so trivially, `InfGrpd` is an `(inf, 1)`-topos. Hence, `InfGrpd` is
for `inf`-groupoids what `Set` is for sets. Without going into detail, intuitively, both are terminal topoi.

As we have previously seen, given a category of presheaves, one can transform it into a category of sheaves by
sheafification. Sheafification is exactly the left adjoint of the inclusion functor from sheaves to presheaves, and it
preserves finite limits, a property we denote as left exactness. In fact, any left exact left adjoint of an inclusion
functor induces a category of sheaves, including for `(inf, 1)`-categories. Its objects are `(inf, 1)`- sheaves, that
is, `inf`-groupoids dependent on context and whose matching families have unique amalgamations, i.e. that glue nicely.

The study of Homotopy Type Theory is the study of the internal language of `(inf, 1)`-topoi, generally denoted as
simply `inf`-topoi. The study of the internal language of `InfGrpd` is simply homotopy theory; Homotopy Type Theory
uses the Curry-Howard-Lambek correspondence in order to construct the type theory whose objects are generalized spaces,
and whose equalities have structure. All `inf`-topoi share basic structure in their internal language, but one is also
able to study specific `inf`-topoi and their particular features.

Do note that, from the perspective of univalent foundations, Kan complexes and quasicategories model `inf`-groupoids
and `(inf, 1)`-categories respectively. In fact, `(m, n)`-categories are the more fundamental object of study, not
any particular model of them. Given a `(m, n)`-category, a simplicial set that models it is called a nerve of the
category. It is a functor `N : C -> [op Simp, Set]` whose left adjoint `R : [op Simp, Set] -> C` is denoted its
realization. By the generalized Yoneda lemma, this perspective does not miss anything about the category in question.
