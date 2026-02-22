## II. 10. Simplicial Sets

A totally ordered set is a poset where any two objects have a morphism. A totally ordered set with `n` objects is
equivalent to the poset of natural numbers smaller than `n`, which we denote as an `n - 1`-simplex. The `0`-simplex
is `0`, the `1`-simplex is `0 -> 1` (the walking morphism), the `2`-simplex is `0 -> 1 -> 2` etc. Consider this shape
geometrically: a `2`-simplex comprises `3` points and `3` edges, so it is a triangle. A `3`-simplex is given by `4`
`2`-simplexes, with any pair corresponding on an edge. This is a polyhedron; simplexes generalize it to `n` dimensions.

Trivially, a simplex is a frame, a locale, a Heyting algebra and a lattice. Treating it as a locale, it ought to
preserve joins and (finite, but simplices are already finite) meets, that is, the ordering. This defines a simplex
category `Simp`. Without loss of generality, we can consider `Simp` to have as its canonical morphisms, families of
form `f : Simp n -> Simp (n + 1)` and `g : Simp (n + 1) -> Simp n`. In fact, we can consider `f` to be monic and `g`
to be epic, and it can be algebraically checked that any morphism is factorized by the canonical morphisms.

Naturally, we can define presheaves `Pr : op Simp -> Set`, whose category form a topos. A monomorphism of form
`f : Simp n -> Simp (n + 1)` is mapped to `Pr f : Pr (n + 1) -> Pr n`, which obtains one of the faces of the simplex.
An epimorphism `g : Simp (n + 1) -> Simp n` is mapped to `Pr g : Simp n -> Simp (n + 1)`, which embeds the `n`-simplex
as a degenerate `n+1`-simplex, given by a selection of face. Such a presheaf is known as a simplicial set. As `SSet`,
the category of simplicial sets, is a topos, it is the case that simplicial sets behave similarly to regular sets.

A simplicial set whose highest non-degenerate simplices are of size `0` is a set. A simplicial set of non-degenerate
`1`-simplices is given by `1`-morphisms whose origin and destination objects might overlap, and whose objects form
degenerate edges: this is a directed multigraph with identities, known as a quiver. As such, simplicial sets generalize
sets and quivers to arbitrarily high dimensions. They do not, however, form `n`-categories by themselves: there is no
definition for morphism composition, or for morphism inverting in order to form `n`-groupoids.

By the density theorem, all simplicial sets are colimits of standard simplices, taken as sets whose objects are faces.
In other words, simplicial sets can be constructed by a combination of coproducts (adding more simplices) and pushouts
(creating equivalence classes on simplices). This tracks geometrically: one can create an `n`-dimensional graph-like
structure by putting together multiple simplices and then gluing points and faces. By gluing two faces of a `n`-simplex,
one degenerates it, by creating an `n`-simplex that is missing a face, or multiple faces if it was already degenerate.

## Horns and Fillers

Let us denote a simplex as a potentially degenerate object of a simplicial set, and the standard simplex as the
canonical version. Given a `n+1`-simplex, its faces are `n`-simplices, and are given by monomorphisms. As this is a
topos, that makes its faces subobjects, and `f` is an injective function to a codomain that is larger by `1`. Thus,
the faces of a simplex are defined by the point they are missing. A Horn `H n k` is defined as an `n`-simplex missing
its `k`-th face, where the ordering is given by the `k`-th point missing in the face. `1`-simplices do not have horns.

Then, given a horn `H n k`, a filling is a monomorphism `f : H n k -> SSet` which fills the face. Visually, it takes
a degenerate simplex and fills its interior. Consider horn `H 2 1`, given by possibly degenerate faces `0 -> 1` and
`1 -> 2`. Then, subject to fulfilling associativity laws, a filling for this horn is morphism composition. Then, for
`H 2 0`, given by `0 -> 1` and `0 -> 2`, a filling yields `1 -> 2`. If we had a face `1 -> 0`, this would be morphism
composition, so filling is finding an inverse. A simplicial set where all horns have fillings is denoted a Kan complex.

## Orientals

A Kan complex is on the right track to modeling an `inf`-groupoid, however, there are two issues: firstly, it is not
clear that associativity holds. Secondly, while `1`-simplices clearly correspond to morphisms, it is not clear in which
sense a `n`-simplex models a `n`-morphism. Note, however, that given two `1`-simplices, their composition is a
`2`-simplex, that is, what we seek to define as a `2`-morphism. Then, composition of `1`-morphisms is given by a 
`2`-morphism we can denote the composer. `2`-morphisms can be composed in two ways, so there ought to be two composers.

`2`-morphism composition is given by `a : f -> g`, `b: f' -> g'`. If it is horizontal, `f = f'`, `g = g'` and
`f, g : C -> D`. If it is vertical, `f, g : C -> D`, `f', g' : D -> E`. The commonality is at follows: for both
`a` and `b`, the origin of their origin is the origin of their destination, and the destination of their origin is the
destination of their destination. This property is inherent to the definition of an `n`-morphism, and as long as it is
maintained, `n`-morphism composition can be constructed component-wise. 

Then, we seek to map each `k`-morphism to its possible sources and destinations. This can be build up constructively:
define `Globes` as the category whose objects are natural numbers, and morphisms `f : Globes n -> Globes (n + 1)` are
given by pairs of functions `(o, d) : n -> (n + 1)` so that for all `(o', d') : Globes (n-1) -> Globes n`, we have
`o' . o = o' . d` and `d' . o = d' . d`. Then, define globular sets as the category of presheaves from `Globes`.
The representable globular set has its objects denoted as orientals, as they orient the simplices.

Consider an `n`-simplex. The `n`-oriental consists of pairs of functions `(o, d) :: [n - 1, n]`. Let us select a pair
`(o_k, d_k) : n - 1 -> n`. Then, `o_k` is an origin face, and `d_k` a destination face, and the `n`-simplex is an
`n`-morphism between the two. This suggests the same `n`-morphism can act as a morphism for different `n-1`-morphisms.
For instance, the compositor of two `2`-morphisms, a `3`-morphism, has two pairs of origin and destination faces.
This tracks with the Eckmann-Hilton argument, where we showed that when they overlap, they are equivalent.

Going back to associativity, consider three `n`-morphisms, `f : C -> D`, `g : D -> E`, `h : E -> F`. This induces
three `n + 1`-morphisms, given by `f . g : C -> E`, `g . h : D -> F`, and one `n + 2`-morphism, given by
`f . g . h : C -> F`. If `n = 1`, this uniquely defines a `3`-simplex, so that associativity holds. Informally, we
expect it holds in the Kan complex whose objects are `n - 1`-morphisms without loss of generality. As such, we have
that a Kan complex is a model for an `inf`-groupoid up to homotopy.

## Kan Complex intuition

The horn-filling condition of Kan complexes does not state that such horns are unique, which is the condition necessary
to model the fundamental groupoid of a topological space. In the context of Homotopy Type Theory, this is precisely
a type, and its objects are terms of the type. Two terms being equal corresponds to a path, that is, an endomorphism,
meaning equality itself is multivalued, and in fact, one can trace paths between equalities ad infinitum. In order to
perform Homotopy Type Theory, we require that `inf`-groupoids themselves form a topos.

Consider the category of Kan Complexes, `KanCplx`. A morphism in this category is an equivalence of Kan complexes up
to homotopy, given by a difference in fillers. Taking the fillers as homotopies, this is a homotopy of homotopies for
all `n`-simplicea of a Kan Complex. This corresponds exactly to fillers, so that `KanCplx` is enriched on itself. In
this sense, there is for any Kan Complex a strict version whose fillers are unique. Thus, given any equivalence in a
Kan complex, it is equivalent to an equality. This is the Univalence axiom: `(a ~= b) ~= (a = b)`.