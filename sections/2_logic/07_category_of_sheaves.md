# II. 7. Category Of Sheaves [WIP]

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
of representable presheaves. This suggests that taking colimits over representable presheaves can act as a method
for constructing new presheaves. In fact, colimits over sieves, which are subobjects of representable presheaves, could
play a similar role. If the construction is able to send presheaves to corresponding sheaves, and also to preserve
finite limits, then we have that the category of sheaves on a site is a topos.

## Sheafification

[TO BE CONTINUED]