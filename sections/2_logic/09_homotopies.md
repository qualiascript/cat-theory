## II.9. Homotopies

A frame is a lattice that has all joins (colimits) and finite meets (limits) and in which the infinite distributive
law holds. That is, given `Y_i`, a collection of objects of the frame indexed by `i`, `x + Lim(Y_i) -> Lim(x + Y_i)`,
taking `x + Y_i` to mean all such joins. In fact, `x + Lim(Y_i) ~= Lim(x + Y_i)` is an isomorphism. This is 
clearly the case for sets and inclusion, but frames generalize beyond sets. Frames are Heyting algebras, so that they
form a CCC. The opposite category of a frame is known as a locale. 

A set-theoretic topology is a subset of a power set equipped with all unions and finite intersections. Then, a
set-theoretic topology, ordered by inclusion, is a frame. However, frames do not require a concept for the elements
of a set. Frames form the 2-category of frames `Frm` and locales from the 2-category `Locale`. A morphism `f : X -> Y`
in `Frm` preserves all joins and finite meets, and so does `f' : Y' -> X'` in `Locale`. Then, a morphism `g : X -> Y`
in `Locale` preserves all joins and finite meets of `Y` within `X`. This is a continuous map.

Given a locale `X`, we denote `O(X)` its opposite category and refer to it as its frame of opens. Given a frame of
opens `O(X)`, one can define a family of covering sieves as sieves, seen as family of morphisms `f_x : U_x -> U`,
so that the join of all `U_x` is `U`. This naturally induces a sheaf topos, and due to the infinite distributivity law,
such topoi are full and faithful to the locales. As such, locales can be seen as a reflective subcategory of `Topos`,
the category of topoi. A reflective subcategory is one whose inclusion functor has a left adjoint.

Given a poset `P`, one can define the slice category `P / y`, which can then be used to define the coslice `x / P / y`.
This is a bislice category, so that its objects `c :: x / P / y` have both morphisms `f : x -> c` and `g : c -> y`.
If `P` is the poset of real numbers, `x` is `0` and `y` is `1`, this is the closed interval `[0, 1]`. This induces
a locale, which we will also denote `[0, 1]`. Then, a morphism `f : [0, 1] -> Y` has the property that all joins
and finite meets are reflected in `[0, 1]`. This is a continuous function, or visually, a path.

## Homotopy

We have previously said that a homotopy is a path between paths. This can be extended to 1-morphisms of `Locale`, which
are continuous maps. Then, given two morphisms `f, g : X -> Y`, a 2-morphism involves morphisms for all `y :: Y` mapped
by `f` to a value `y' :: Y` mapped by `g`. Each such path is given by `f_y : [0, 1] -> Y`, so that `0` is mapped to `y`
and `1` to `y'`. This induces a morphism `h : X * [0, 1] -> Y`, so that there are `f', g' : X -> X * [0, 1]` such that
`f' . h = f` and `g' . h = g`. A morphism `h : X * [0, 1] -> Y` with this property is known as a homotopy.

Intuitively, it is useful to think of `h : X * [0, 1] -> Y` as a timestamped continuous map. At time `0`, it is `f`, and
at time `1`, it is `g`. `X * [0, 1]` is known as a cylinder object, as it extends `X`, visualized as a circle, along the
`[0, 1]` axis. Both spatial and temporal dimensions can be useful for topological visualization. It induces two maps,
`a : X + X -> X * [0, 1]`, which maps values at both ends of the cylinder, and `b : X * [0, 1] -> X`, which collapses
the cylinder. Note that if `X = 1`, the cylinder object is `[0, 1]`, which is simply induced by the `Locale` 2-category.

If a homotopy is given by `h : X * [0, 1] -> Y`, we can simply apply the definition again to obtain that a homotopy
between homotopies is given by `h : X * [0, 1] ^ 2 -> Y`. In fact, this can be repeated ad infinitum. This would
suggest that `Locale` forms an infinite-category, however, we do not have a categorical model for this concept. In fact,
each `n`-homotopy also induces equivalence clases, which would collapse an `n`-category to an `n-1`-category. This
indicates a deep connection between homotopies and higher category theory, but it is still unclear in what manner.

In fact, there is one fact that has remained unused so far: every homotopy is a path, and every path is invertible.
A continuous map `f : X -> Y` is not necessarily invertible, but `[0, 1]` is naturally isomorphic to its own opposite,
so that the homotopies we discussed are denoted left homotopies, with an opposite right homotopy. Then, homotopies do
not induce merely infinity-categories, but in fact, infinity-groupoids, by taking the 0-cells to be points in a space,
1-cells to be paths between points, and `n`-cells to be `(n-1)`-homotopies. This is known as the Homotopy hypothesis.

## Fundamental groupoids

Given a topological space, such as a locale, one can form its fundamental groupoid by letting the objects be points
and the morphisms be paths between points. If two spaces have naturally isomorphic fundamental groupoids, they are
equivalent up to homotopy. This is a trivial consequence of homotopies being 2-morphisms. By similar logic, if two
spaces have isomorphic fundamental `n`-groupoids, they are equivalent up to `n`-homotopy. Thus, the fundamental
infinity-groupoid of a space is sufficient to define the space up to any homotopy level.

Given a space and a point of the space, one can define its fundamental group at the point, as a group is a one object
groupoid. This is done by tracing its endomorphisms, which can traverse other objects before returning. If the
fundamental groupoid is 0-connected, its fundamental group does not depend on the choice of point. Similarly, if the 
fundamental groupoid is `n`-connected, its fundamental `(n+1)`-group is uniquely defined. The fundamental group of a
circle is the set of integers equipped with addition, as one can perform laps in either direction any number of times.

Then, homotopies provide the right semantics for infinity-groupoids, and infinite-groupoids model spaces up to any
homotopy level. This suggests taking a geometric approach to constructing infinity-groupoids. The inspiration comes
from infinity-dimensional Euclidean geometry: using regular polygons, one can construct elaborate n-dimensional shapes,
which can then act as homotopy equivalents for any topological space. This requires careful formalization, but if it is
possible, it provides the necessary semantics for a categorical construction of infinity-groupoids.