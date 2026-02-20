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
is a possibly degenerate triangle. `Pr 3` is a tetrahedron and `Pr n` is an n-dimensional shape with `Pr (n-1)` faces.

Also consider `g : Simp (n + 1) -> Simp n`. This mapping can be considered surjectively without loss of generality.
It is a choice of which two objects of `Simp n` get overlapped. Then, `g' : Pr n -> Pr (n + 1)` is a map of the
n-dimensional shape, known as simplexes, to a `n + 1`-simplex, for instance, embedding a triangle as a degenerate
tetrahedron for each possible degenerate node. The presheaf is known as a simplicial set, morphisms
`f : Pr -> Pr (n - 1)` are face maps, and `g : Pr (n + 1) -> Pr n` are degeneracy maps. It is a generalized quiver.

## Kan Complex

[TO BE CONTINUED]