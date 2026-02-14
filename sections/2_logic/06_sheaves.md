# II. 6. Sheaves

The motivation for topology lies in the study of continuous objects, the simplest case being functions. A continuous
function over real numbers is easily definable by using the fact that the real numbers line is a metric space, that is,
a space with a suitable concept of distance between any two points. This is not necessarily the case: the famous example
of a coffee mug transforming to a torus is not really about deforming shapes, but about sufficiently deformed spaces.
As it turns out, topology merely requires a concept for closeness, which can be constructed categorically.

The first important construction towards categorical topologies is the sieve. A sieve is a subobject of a representable
presheaf. In other words, it is a monic natural transformation into `hom(-, x)` for some `x :: C`. This selects some,
but not necessarily all, of the elements of the presheaf, which are morphisms. Due to the presheaf being a contravariant
functor, it also maps all elements with the origin being an element of the homset in the opposite category, or in other
words, all morphisms whose destination is a morphism of `hom(-, x)`. As it is monic, these are preserved.

Then, a more practical definition for a sieve is as a subobject of the slice category `C / x` with the property that
if `f : y -> x` is a morphism of the sieve, then for any `g : z -> y`, `g . f` is also a morphism of the sieve. It is
a collection of morphisms that is closed under precomposition. Visually, it is a tree-like structure where the direct
children of the root node are maximally expansive within the category. Topologically, this constructs a collection of
generalized elements of an object, with the property that these elements themselves have all their generalized elements.

## Grothendieck Topology

A topology in set theoretic terms is a subset of a power set that is closed under unions and finite intersections. As
a consequence, two of its elements, known as open sets, are the terminal object, or the set which induced the power set,
and the initial object, which is the empty set. Each open set represents a selection of elements which we deem to be
"close". Categorically, this is modeled by a lattice, whose unions are joins (coproducts), intersections are
meets (products) and morphisms are inclusions. In fact, this is a complete lattice, with all joins and meets.

Given some open set, an open cover is a collection of open sets whose union is the original open set. Within the
lattice, the intersection of open sets also form open sets, so that an open set can be conceptualized as the union of
some, but not necessarily all, of a given open set's elements. This is exactly a sieve, and its elements form an open
cover of the sieve. This is, in fact, more general and can work on categories that are not sets. This suggests that a
categorification of topologies could be defined in terms of sieves.

In order to define such a topology over `C :: Cat`, we seek to assign any `x :: C` a collection of covering sieves
which preserve meets and joins. Firstly, we can meet zero objects to get the terminal object `id (hom(-, c))` which is
always a covering sieve. Meets are pullbacks over the underlying objects, so that we have all base change functors.
If we have a morphism `f : y -> x`, we can apply the base change to all morphisms of a covering sieve on `x` to obtain
a new sieve. Naturally, this ought to be a covering sieve of `y`. This is denoted base change stability.

Consider a sieve on `x`, but not necessarily covering `x`, denoted `F`. When base changing `F` along morphisms of form
`g : z -> x`, some induced morphisms cover `z`. Let's say there is a sieve `G` composed of some of these morphisms
which covers `x`. We can obtain `F` back by performing a union with the sieves that weren't selected, so naturally,
`F` must cover `x`. This is known as the local character condition. If the family of covering sieves respects this
condition, along with base change stability and the existence of identity sieves, it is denoted a Grothendieck Topology.

## Sheaves

The pairing of a category `C` with a Grothendieck topology `J` is denoted a site. Due to base change stability, `J`
can be considered as a presheaf `J : Op C -> Set` mapping objects `c :: C` to covering sieves on `c`. Then we have that
component-wise, `J(c)_i : U(c)_i -> Yo c`, where `U(c)_i` is a family of morphisms with destination `c`. Let us also
denote `Psh(C) = [op C, Set]` as the category of presheaves for `C`, so that `Psh` is a functor. A presheaf
`Sh : op C -> Set` is a sheaf if and only if for all `J(c)_i`, `hom_{Psh(C)}(-, Sh) J(c)_i` is an isomorphism.

Let us unpack this. `hom_{Psh(C)}(-, Sh) : op(Psh(C)) -> Set` is contravariant, so `J(c)_i :: Psh(C) ^ I` applied to it
inverses the morphism. Let us denote `M` the result, `M : hom(Yo c, Sh) -> hom(U(c)_i, Sh)` an isomorphism. By the
Yoneda Lemma, `Sh c ~= hom(U(c)_i, Sh)`. Note that this is the case for all coverings `U(c)_i`. Then, the sheaf must
agree on all such covers. In other words, if `Sh` is a sheaf over site `(C, J)`, it maps any `c :: C` to a natural
transformation that maps the elements of all covers of `J` to elements of `Sh` in a globally coherent manner.

## Sheaves Intuition

Sheaves are oftentimes described in terms of locality and gluing conditions. These fall naturally from the categorical
definition, but it's worth making explicit. Locality says that if two sieves are mapped by the sheaf in agreement at
all elements, they are isomorphic. Gluing states that if a family of sieves are mapped by the sheaf in agreement at
all intersections, the union sieve is also in agreement with all the sieves that constructed it. The latter is what
makes sheaves represent continuity. It is immediately apparent that the categorical sheaf respects these conditions.

Since sheaves are comprised of natural transformations, they are given component-wise. For each `f :: U(c)_i`, so
that `f : b -> c`, `Sh c f` maps it to some `d :: Sh c`. This mapping is global to all sieves at `c`, but also coherent
locally for each individual sieve. The sheaf can significantly alter the topology, to the extent that the image of
an object through a sheaf can have properties that the underlying object does not. For an intuitive example, a Möbius
strip is isomorphic to a circle from the perspective of its unique edge, but has non-trivial structure in its topology.