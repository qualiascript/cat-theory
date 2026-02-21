## II. 10. Simplicial Sets

A totally ordered sets is a poset so that all objects have a morphism between them. In ZFC, natural numbers are defined
so that if `a < b`, then `a` is a subset of `b`. Then, for any value `n :: FinSet`, every totally ordered set is
isomorphic to the poset given by initial object `0`, terminal object `n` and morphisms as set inclusion. Then, we have
a function `F : FinSet -> OSet`, which maps natural numbers to ordered sets. In fact, we seek for this function to be
a functor. A morphism between totally ordered sets is a mapping that preserves limits and colimits, that is, the order.

A simplex category is such a category, with the added stipulation that `F n` has morphisms only to `F (n-1)` and
`F (n + 1)`. We denote this category `Simp`. Then, consider a presheaf `Pr : op Simp -> Set`. This maps `Simp n` to
a set, each morphism `f : Simp (n - 1) -> Simp n` mapped contravariantly to `f' : Pr n -> Pr (n - 1)`, and morphisms
`g : Simp (n + 1) -> Simp n` mapped to `g' : Pr n -> Pr (n + 1)`. In fact, `f'` and `g'` are functions, so that one
can speak concretely of their mapping of individual elements in the presheaf's set mappings.

Let us start with `f : Simp (n - 1) -> Simp n`, in fact, `f : Simp 0 -> Simp 1`. Diagrammatically, this is a mapping
from `0` to `0 -> 1`, and there are two such mappings for the two objects. As such, there are two morphisms
`f' : Pr 1 -> Pr 0`. If one considers `Pr 0` as a set of points, `Pr 1` is mapped to points in two ways. Then, `Pr 1`
is visually an edge, with the stipulation that its two nodes might overlap, and two edges can share the same underlying
nodes in any manner. This is precisely a directed multigraph defined categorically. It is also referred to as a quiver.

Then consider `f : Simp 1 -> Simp 2`. It is a mapping of `0 -> 1` to `0 -> 1 -> 2`. Without collapsing objects, there
are three such maps, and if the objects get collapsed, they are isomorphic in the presheaf, so that the node is really
just a degenerate edge. Then, without loss of generality, let us consider the three injective maps. This forms a shape
composed of three edges, `0 -> 1`, `0 -> 2`, `1 -> 2`, and by tracing its points, `0`, `1` and `2` must overlap. This
is a possibly degenerate triangle. `Pr n` is an n-dimensional shape with `Pr (n-1)` faces, known as a simplex.

Also consider `g : Simp (n + 1) -> Simp n`. This mapping can be considered surjectively without loss of generality.
It is a choice of which two objects of `Simp n` get overlapped. Then, `g' : Pr n -> Pr (n + 1)` maps an `n`-simplex
to a degenerate `n+1`-simplex, such as a triangle to a degenerated tetrahedron, for each face that could overlap.
The presheaf is known as a simplicial set, morphisms `f : Pr -> Pr (n - 1)` are face maps, and `g : Pr (n + 1) -> Pr n`
are degeneracy maps. This forms a generalized quiver, corresponding to higher categories.

## Kan Complex

Let us denote `SSet = [op Simp, Set]` the category of simplicial sets. This is a category of presheaves, so it is a
topos. Its subobject classifier is given by the Yoneda embedding of `Simp`, so that by treating `Simp n` as the
standard `n`-simplex, the objects are its faces. By the Density Theorem, every simplicial set is a colimit over
its simplices, when treated as a category whose objects are faces. Then, for `S :: SSet`, we can without loss of
generality denote `S n` as a set of `n`-simplices, whose objects `o :: S n` are faces of the `n`-simplex.

Then, we can safely treat `SSet` as if it were a category of sets, remembering that excluded middle does not hold. 
Let us denote `Sim n` the standard `n`-simplex, so that `Sim` is the Yoneda embedding of the simplex category.
Naturally, there is a subobject `H n k`, which has all faces of `Sim n` except the `k`-th one. This is denoted as a
horn, as it is a type of degenerate simplex. Note that `Sim 0` trivially has no horns. Given a horn `H n k`, if there
is a morphism `f : H n k -> Sim n` so that the canonical `g : Sim n -> H n k` is a section, it is known as a filler.

A Kan Complex is defined as a simplicial set where all horns have fillers. This can be conceptualized constructively:
a Kan complex is a simplicial set equipped with a surjective function `f : FinSet -> Set`, mapping to a set of fillers
for each simplex dimension. Clearly, Kan complexes exist for any simplicial set. Consider a `2`-horn. Let us order the 
faces so that the `k`th face is the one that lacking `k` in its composition. Then, we have `H 2 0` missing `1 -> 2`,
`H 2 1` missing `0 -> 2` and `H 2 2` missing `0 -> 1`. Consider what it means for each to have a filling.

For `H 2 1`, we have `f : 0 -> 1`, `g : 1 -> 2` and can obtain `h : 0 -> 2`. This is akin to morphism composition,
however, it is not yet clear that this operation is associative. Let us assume it is for now. Then consider `H 2 0`,
so that we have `f : 0 -> 1` and `h : 0 -> 2`. If `f` had an inverse `f' : 1 -> 0`, then we could define the composition
`f' . h` to obtain `g`. Then, practically, this is the action of the horn filling, and as this is a generic argument,
assuming associativity, a Kan complex limited to at most `2`-simplices would form exactly a groupoid.

## Orientals

It is important to clarify in what sense we are taking `k`-simplices as `k`-morphisms. A `k`-morphism has an origin and
a destination, which are `k-1`-morphisms, but the `k-1`-morphisms in question have the same origin and destination.
Then, if for `S :: SSet`, `Or n : S (n+1) -> S n` mapping to origin and `De n : S (n+1) -> S n` mapping to destination,
we have that `Or (n+1) . Or n = De (n+1) . Or n` and `Or (n+1) . De n = De (n+1) . De n`. In fact, as long as this
property holds, `k`-simplices can act as `k`-morphisms. Intuitively, this matches the Eckmann-Hilton argument.

Let us construct exactly this category. The category `Globes` is defined on objects as `Globes n = FinSet n`, and the
morphisms are of form `f : Globes n -> Globes (n+1)`, given by pairs of functions `(So n, De n) : n -> n + 1` with the
property that, for any `g : Globes (n-1) -> Globes n`, given by a pair `(So (n-1), De (n-1))`, we have that
`So (n-1) . So n = So (n-1) . De n` and `De (n-1) . So n = De (n-1) . De n`. Then, let us equip each standard
`n`-simplex with its `Globes (n-1)` origins and destinations. This is denoted an oriental, as it orients the simplex.

The first oriental (corresponding to `0`-simplices) sends a point to an origin and destination, which we can assume
different (degeneracy is fine, it corresponds to identity morphisms). Up to isomorphism, it is `0 -> 1`. The second
oriental sends two edges to a triangle in a coherent manner, which can be checked to be `0 -> 1` and `1 -> 2`. The
third oriental has two options: either `0 -> 1 -> 2` or `1 -> 2 -> 3` can act as an origin. This implies `2`-morphisms
have two different compositions, which is correct. The fourth ordinal induces five compositions.

In fact, consider three morphisms, `f : 0 -> 1`, `g : 1 -> 2`, `h : 2 -> 3`. This induces composite morphisms
`f . g : 0 -> 2`, `g . h : 1 -> 3` and `f . g . h : 0 -> 3`. This forms a `3`-simplex, so that associativity is not
just true up to isomorphism, but, in fact, an equality. In fact, each `1`-morphism composition yields a `2`-morphism
as a composer, and each composer yield a `3`-morphism known as an associator in two different ways. Similarly, the
composition of any `k`-morphisms is associative. Thus, a Kan complex is a model for a strict infinity-groupoid.

In a Kan complex, an equivalence is given by any `k`-morphism. But as it is a strict model, such an equivalence within
the internal language of the Kan complex, is, within the language of category theory, isomorphic to an equality of sets.
In other words, equivalence is equivalent to equality, or `(a ~= b) ~= (a = b)`. This is known as the univalence axiom.
It is the fundamental building block of the Univalent Foundations project, and forms the basis for Homotopy Type Theory.
