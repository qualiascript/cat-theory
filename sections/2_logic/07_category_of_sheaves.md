# II. 7. Category Of Sheaves

We would like to show that, given a site, its category of sheaves is a topos. Firstly, let us show that a category
of presheaves `Psh(C)` is a topos. We need a subobject classifier on presheaves. Consider the meaning of a monomorphism
in the category of presheaves: it is a natural transformation given by monomorphisms on sets component-wise. Some
sheaves are representable, whose subobjects are sieves. Given `J : Op C -> Set` the presheaf that maps to covering
sieves, `hom(Yo c, J) ~= J c`. This is a subobject classifier in this case, and we must show it is in general.

Then, for `Om = J`, `true : 1 -> Om` selects the terminal object of `Om`. For each `c :: C`, the terminal object of
`Om c` is the maximal sieve, given by the identity morphism. Then, we must show that for any presheaf `F :: [op C, Set]`
with subobject `G : R -> F`, there is a morphism `M : F -> Om` so that `G = Pb(M, true)`. Component-wise, 
`M_x : F x -> Om x` maps each `F x y` to a sieve. `Pb(M, true)` consists of subobjects of `F x` mapped to the maximal
sieve. Then, `M_x` must map `F x y` to the maximal sieve if and only if `y :: G x`.

Given some morphism `f :: C ^ I`, `f : d -> c`, for some `x :: d`, `a = F f x :: F c`. Then, for each `c` and `a`,
construct a sieve `Sv_c_a` which includes `f` if and only if `a :: G c`. This can be constructed using pullbacks.
If the sieve is maximal, all generalized elements of `F c` are included in `G c`. Then, let us set `M` to map to such
sieves. By checking the naturality condition, one observes that `M` is unique up to isomorphism. Thus, the category
of presheaves has a subobject classifier. Then, if it is also a CCC, it is a topos.

Presheaves are functors, which are categories, and the product of categories is the Cartesian product of their
underlying object sets and homsets. Then, given two presheaves `F, G : op C -> Set`, `(F c) * (G c) = (F * G) c`.
Pullbacks can be induced by constructing the power objects. Then, we need a suitable construction for exponents,
so that `hom(A * B, C) ~= hom(A, C ^ B)`. If `A` is representable, we get that `(C ^ B) x = hom((A x) * B, C)`. This
is a full definition for a presheaf, and one can check the adjunction holds in general. Thus, `Psh(C)` is a topos.

## Density Theorem

Given a presheaf `Pr : 1 -> Set ^ (op C)`, consider the comma category `Yo \/ Pr`. Its objects are elements `Pr(c)(x)`,
which can be envisioned as pairs `(c, v) :: C * Set`. There is a canonical functor `F : C * Set -> C` that forgets the
second value. Then, let us denote `G : [op C, Set] -> [op C, Set]` `G X = (Yo \/ X) . F . Yo`. We have
the following property, known as the Density Theorem: for any presheaf `Pr`, the colimit over diagram `A = G Pr`
is isomorphic to `Pr`. In order to prove this, we will be using the adjunction property.

We have that `hom(Pr, B) ~= hom(A, Diag_B)`. On the left, we have natural transformations `N : A -> Diag_B`. Consider
`N_c_v : A (c, v) -> Diag_B (c, v)`, for `(c, v) :: C * Set`. This becomes `N_c_v : Yo c -> B`, so `N_c ~= B c`.
Then, a natural transformation `M : Pr -> B`, given as `M_c : Pr c -> B c`, is isomorphic to an `u : 1 -> B c`. Natural
transformations between presheaves have exactly this property, as shown in the proof for the Yoneda Lemma. Thus,
the natural isomorphism is correct, and for any `Pr :: [op C, Set]`, `Pr = Colim (G Pr)`.

But recall that `G Pr` sends a presheaf to a diagram that selects Yoneda embeddings. Thus, every presheaf is a colimit
of representable presheaves. This implies that taking colimits over representable presheaves can act as a method
for constructing new presheaves. Then, we should explore whether taking colimits can also construct sheaves. If the
construction is able to send presheaves to corresponding sheaves, and also to preserve finite limits, then we have that
the category of sheaves on a site is a topos.

## Sheafification

For some site, consider `J c`, the covering sieves on `c`. They naturally form a poset by inclusion, and they also
induce matching families, but the two are contravariant. Then let us define `Match_c` as a presheaf from the covering
sieves on `c` as a poset to the set comprised of the sieve's matching families with some presheaf `Pr`. Intuitively,
a colimit over `Match_c` would create equivalence classes over sets of matching families, which seems to be on the
right track for constructing a sheaf. We denote this construction `Pr+`, so that `Pr+ c` is the colimit over `Match_c`.

As it is a colimit, the elements of `Pr+ c` are equivalence classes of matching families. The equivalence classes are
given by reverse inclusion, so that any two matching families that restrict to the same matching family are equivalent.
This means that any amalgamation on each matching family is unique, as a different amalgamation would define another
matching family, but the two have been made equivalent. One can also check that `Pr+` is indeed a presheaf. However,
it is not necessarily a sheaf: we have not demonstrated that each matching family does have such an amalgamation.

`Pr+` is denoted as a separated presheaf. In fact, `Pr++` is a sheaf. This can be shown as follows: consider what
`Pr++` entails on the maximal sieve: it is a collection of matching families so that any amalgamation is unique. They
are to be made equivalent, so that if any such matching family has an amalgamation, this yields a sheaf. In fact, such
an amalgamation ought to exist, given by a representable presheaf which is trivially a sheaf. Then the maximal sieve
has an amalgamation, and so do all covering sieves by base change. Thus, `Pr++` is a sheaf.

Then, for `Pr` any presheaf, `Pr++` is denoted the sheafification of `Pr`. If `Pr` is already a sheaf, it leaves it
unchanged, and as sheaves are by definition presheaves, this suggests that the specification on all objects in a
category of presheaves, given some site, yields a category of sheaves. The plus construction also preserves limits;
proving this is beyond the scope, but it stems from matching families having all cocones, which makes it a filtered
colimit. Filtered colimits preserve limits, and as such, the category of sheaves is a topos.

In fact, sheafification is left adjoint to the inclusion functor which maps each object in the category of sheaves
to its canonical object in the category of presheaves. This can be shown as the unit of the adjunction can be simply
given by identity, and the counit sends a presheaf to its canonical sheaf representation, viewed as a presheaf.

## Sheaf Topos intuition

By the Density Theorem, every sheaf is a colimit over representable presheaves, which themselves are sheaves. As the
category of sheaves is a topos, all finite limits and colimits on sheaves are also sheaves. The subobject classifier
is given by `J`, which maps elements to covering sieves, which is already a sheaf by the definition of Grothendieck
topologies. The construction for exponential objects also remains the same, and always yields a sheaf. In general,
this implies that one can do mathematics on sheaves, similar to if they were sets.

In fact, a trivially valid site is given on the category `1` by covering sieves `0` and `1`. Plugging this in, a sheaf
`Sh : 1 -> Set` is exactly a set, and the sheaf topos is reduced to a set topos. This illustrates that the sheaf topos
is a formal model for sets whose values depend on objects in a well-behaved manner, which is exactly what a sheaf is.
In a sheaf topos, truth is multivalued, but `TRUE` corresponds to the maximal sieve, or universal truth. However,
excluded middle does not hold: a property that does not hold globally does not necessarily hold locally either.