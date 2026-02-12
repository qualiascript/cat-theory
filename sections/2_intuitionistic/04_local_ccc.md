# II.4. Locally Cartesian Closed Categories

Previously, we have assumed that a given slice category `C / x` has products and internal homsets. This is not
immediately given. Let us define a Locally Cartesian Closed Category (henceforth a LCCC) to be a category `C :: Cat`
with a terminal object so that every slice category `C / x` for `c :: Cat` is a CCC. Then, `C / 1 = C` is also a CCC,
so that any LCCC is a CCC. Just like CCCs have their internal logic be equivalent to simply typed lambda calculus,
LCCCs provide a model for dependently typed programming languages, although not the strongest one.

Consider the meaning of a product in `C / x`. The product of `A : a -> x`, `B : b -> x` is `P : p -> x` so that
a morphism `f : Z -> P` is equivalent to two morphisms `g : Z -> A`, `g' : Z -> B`. The naturality condition of the
slice category implies these morphisms induce a commutative diagram with a universal property for any `Z`, so that
`A * B` in the slice category is the same as the pullback of `A` and `B` in `C`. Products in `C / 1` are trivially
products in `C`. Then, an LCCC admits all finite  products and pullbacks, and as such, it is finitely complete.

Then the product `A * B` is given by `Q : Pb(A, B) -> X`, which is given by two projections `M : X -> a`, `N : X -> b`
so that `Q = M . A = N . B`. Consider the functor `- * B : C / X -> C / X`. Given some `A`, `A * B = N . B`. This
is the composition of two functors, `BC_B : A -> N` and `DS_B : N -> N . B`. If both have a right adjoint, then
`- * B = BC_B . DS_B` has right adjoint `BC_B . DP_B` (note the inverting). Applied to some `A`, `BC_B A` yields
`P : Pb(A, B) -> B`. Then, we ought to consider the value of `DP_B P`.

`DP_B P` is a family of local sections of `P: Pb(A, B) -> B` for each fiber of `B : b -> X`. That is, it is a selection
of morphisms `F : B -> Pb(A, B)` so that `F . B = id B`. This is simply a mapping of each element of `A` to an element
of `B` at the corresponding fiber. In other words, `(BC_B . DP_B) A = B ^ A`. This assumes the right adjoints exist:
the dependent sum always exists in a comma category, and its right adjoint is the base change functor. Thus, a LCCC
is alternatively a category with all pullbacks, all dependent products and a terminal object.

## Semantics of LCCCs

By the Curry-Howard correspondence, if `C` is a CCC, we have that `A * B` is an `AND` operation, `A -> B` (as in
`[A, B]`) is an `IMPLIES` operation, and the terminal object is `TRUE`. Furthermore, if it is an LCCC, the base change
functor is a substitution, dependent products are universal quantifiers, and dependent sums are existential
quantifiers. We also have that `C` has all finite limits. What is currently missing are coproducts, corresponding to
`OR`, or more generally, colimits. An LCCC that is finitely cocomplete is denoted as a Heyting category.

In a Heyting category, we have that pullbacks preserve colimits. That is because pullbacks are given by Base Change
functors, which are left adjoint to dependent products. It is oftentimes the case that left adjoints preserve colimits
and right adjoints preserve limits, that is, if `F` is a left adjoint, `F(Col x) = Col (F x)`. Then, every slice
category of `C` has is finitely bicomplete. For `C` a Heyting algebra, and `x :: C`, let us explore the properties
of the slice category `C / x`. 

In `C / X`, `A -> B` is always definable, but it might not necessarily be inhabited: not every statement implies
another. We know that the terminal object is implied by everything, and the initial object implies everything. Then,
let's define a category that has a morphism `f : A -> B` if and only if `A -> B` is inhabited. This is a thin category,
meaning a category where all morphisms with the same origin and destination are equal. Limits and colimits in this
category correspond to limits and colimits in the slice category, so it is a finitely bicomplete CCC.

This new category is known as a Heyting algebra. Let us also declare that in a Heyting algebra, isomorphic objects
are equal. One could construct such a category by creating a quotient set of the original category's object set.
A category with this property is known as a skeletal category. Any thin category induces a preorder, and thin skeletal
categories are known as posets. A poset that has all finite products and coproducts (known as meets and joins) is also
known as a lattice. As the category is thin, this is in fact the same as all finite limits and colimits.

Then, a Heyting algebra is a lattice that is also an CCC. As any internal homset can be obtained as a result of the
product-exponent adjunction in a CCC, the existence of the product-exponent adjunction is enough to demonstrate that
a lattice is a Heyting algebra. The internal homfunctor of a Heyting algebra is known as implication, and as such,
we derive that a Heyting algebra is a lattice where `(A AND B) -> C = A -> (B -> C)`. Trivially, this
property logically holds in mathematical deduction.

Then, Heyting Categories have the property that any slice of the category, taken as a poset, is a Heyting algebra. 
Thus, Heyting algebras represent a model of intuitionistic logic. The initial object is `FALSE`, which implies anything,
but in fact every false statement implies everything, including `FALSE`, and no true statement implies `FALSE`. Then,
we can define the negation operation as simply `NOT X = X -> FALSE`. However, we do not have that `NOT NOT X -> X` by
necessity. This is known as the law of excluded middle, and a Heyting algebra that respects it is a Boolean algebra.

## Heyting Categories as Dependent Types

Using the logic of Heyting algebras, let us look at base changes, dependent products and dependent sums in more detail.
A base change is a substitution: take dependent types as propositions indexed by values `P(x)`, then if `P(x)` is
inhabited and `F(x)` is inhabited, so is `P(F(x))`. Dependent sums are propositions of type `EXISTS F(x) -> P(x)`,
which are inhabited if `P(x)` is inhabited over the domain of `F(x)`, meaning, if `(P . F) x` is inhabited. This
recovers the categorical derivation of dependent sums as morphism composition.

Dependent products are of type `ANY F(x) -> P(x)`. Recall that `F(x)` is a dependent type, and as such, it is in
general multiply inhabited at `x`. This is a specific construction `y` which acts as a proof for `F(x)`. Then,
if the dependent product is inhabited at `F(x)`, every `y` is mapped to an inhabitant of `P(y)`. In other words,
the dependent product is inhabited by methods by which `P` is true for all inhabitants of `F` at `x`. If there is
at least one inhabitant, there is such a mapping, and as such, it is true that for any `x` so that `F(x)`, `P(x)`.

However, Heyting categories are not by themselves sufficient to represent all of Intuitionistic Logic. We are lacking
a suitable construction for representing subobjects. A subobject is the categorification of a subset, and it can be
represented as a monomorphism. We seek a subobject classifier, a method of describing subobjects in the internal
language of a category. If a Heyting category has a subobject classifier, it is known as a Topos. Topos, plural
Topoi, are a place to do mathematics in. They are what this entire guide has been building towards.
