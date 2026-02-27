# II. 12. Kan Fibrations

The definition of a Kan Complex is that of a simplicial set where all horns have fillers. If `S` is a simplicial set,
selecting a horn is akin to a function `f : H n k -> S`, and a filler is a function `g : H n k -> Simp n`. Then, in
order for all horns to have fillers, any such `f` must induce a morphism `l : Simp n -> S` so that the diagram
commutes. The morphism `l` is known as a lift, as it lifts the filler, which is a morphism to a standard simplex, to
the structure of `S`. However, this is a trivial lift, as it induces no conditions on the filling property.

We can reframe this as follows: a simplicial set is not dependent, so it is a morphism `S : y -> 1`to the terminal
object in `SSet`. Instead, let us set `S : y -> x`, so that `S` is in the slice category `S / x`. Then, consider the
commuting diagram formed by `f : H n k -> y`, `g : H n k -> Simp n`, `h : Simp n -> x` and `S`. Then, a lift
`l : Simp n -> y` which makes the diagram commute lifts a filler on `x` to a filler on `y`, which depends on `x`. If
all such lifts exists, `l` is a Kan fibration. A Kan complex is a `s :: SSet` so that `S : s -> 1` is a Kan fibration.

Clearly, the commuting square is given by a fiber product of `S : y -> x` and `h : Simp n -> x`, and each such pullback
induces a morphism `l : Simp n -> y`. In other words, `l` is the result of base changing `h` along `S`. This is the
case for every horn-filling `h`, that base changing preserves a full simplex morphism. This is the context in which
`S` is a fibration: every subobject of `x`, except for points which have no horns, can be canonically pulled back to a
subobject `y` by the fibers of `S`. Topologically, `S : y -> x` is a continuous map that is epic on all paths of `x`.

## Kan Fibrations Examples

Trivially, the empty bundle `S : 0 -> x` is a Kan fibration, as there is nothing to lift. An inner Kan fibration is
akin to a Kan fibration, but without the requirement of lifting horn-fillings for the first and last horns. Similarly,
a left Kan fibration is a Kan fibration without necessarily lifting the last horn, and a right Kan fibration, the left
horn. Kan fibrations are stable under pullback, meaning pulling back with any Kan fibration yields another Kan
fibration. In fact, all `inf`-topoi have universal Kan fibrations, which recover all Kan fibrations by pullback.

Visually, a simplicial set is given by a gluing of standard simplices, and as such they have a boundary, given by the
shape without its interior. For instance, the boundary of `Simp 2` is a triangle. More formally, it is a monomorphism
into a `n`-simplex that excludes the unique `n`-cell. Given a Kan fibration `S : Y -> X`, it is denoted as trivial if
for `a, b :: Y` so that `a . Y = b . Y` and for boundaries `B_a`, `B_b`, there is a value `i` so that `B_a i = B_b i`,
then `a = b`. Visually, for each fiber of `X`, the gluing is trivial: simplices are either unglued or equal.

## Circles and Intervals

As we established, the `inf`-groupoid of the circle is given by the set of integers `Z`, with paths as addition. In the
category `InfGrpd`, a circle can be defined as the pushout of the terminal object `1` with itself. We use that in a CCC,
`a ~= 1 -> a` to obtain a diagram `Di 2 -> 1`, `Di x = 1`. The pushout, which in this specific case is a coequalizer,
induces a path `1 -> 1`. This path can be composed with itself, and has an inverse, so that this yields all integers.
Then, `Z = Po(1, 1)` is a circle up to homotopy. It is a degenerate `1`-simplex where the `0`-cells coincide.

Consider `Simp 1`, the standard `1`-simplex which is isomorphic to the walking morphism `I`. From this perspective,
it is also the walking path, or the walking equality. Then, a path is given by `F : I -> C`, so that in topological
terms, `I = [0, 1]`. Hence, the walking morphism is also called the interval object. By the properties of `inf`-topoi,
for any space `X` we can define space `X ^ I`, which is a space of paths, so that `X ^ I` is denoted a path space
object. This is a subspace of `X * X`. Then, a path between paths is given by `X ^ I ^ I ~= X ^ (I * 2)`.

Note that the fundamental `inf`-groupoid of `I` is isomorphic to `1`, which is the terminal `inf`-groupoid. If `X` is a
space and the unique morphism `f : X -> 1` is a homotopy, such a space is deemed contractible. Recall that we have
shown that `1` is the `(-2)`-groupoid, and equivalent to the value `TRUE`. By comparison, an `(-1)`-groupoid is either
contractible or uninhabited, that is, either `TRUE` or `FALSE`. A `(-1)`-groupoid is contractible if it is inhabited.
We denote a space `k`-truncated if it is equivalent to a `k`-groupoid, so that contractible spaces are `(-2)`-trucated.

## Higher Inductive Types

Inductive types are the types given by initial algebras. Higher inductive types are given by initial algebras in an
`inf`-topos. In particular, the circle and interval constructions yield circle and interval types, by the initial
algebra on a suitable endofunctor. An important construction, related to interval types, are identity types, which
simply yield that points are identical to themselves. Using identity types, one can express inductive type that are
given by `k`-cells for any `k`. In pseudocode, they can be defined as follows:

```
Inductive infix = :: A -> A -> Type :=
    idpath := forall (x :: A), x = x
```

Breaking this down, `=` is a type parametrized by two values `x, y :: A`, and `idpath` is required to be given in order
to construct `=`. It is an infix type, so that one writes `a = b`. Then, `idpath` takes any value `x :: A` and, using
dependent products, constructs `x = x`, which is an inhabitant of `=`. The recursive definition functions due to it
being an initial algebra, and as such being defined by having fixed points. `Type` is a type universe, which contains
all types that do not depend on `Type` itself. Then, the interval and circle types are as follows:

```
Inductive Interval :: Type :=
    0 :: Interval
    1 :: Interval
    path := 0 = 1
    
inductive Circle :: Type :=
    base :: Circle
    lap := base = base
```

In this case, we assume that the `=` type can infer that `idpath` is implicitly used. This is a highly informal example
of Homotopy Type Theory, which ought to be studied as a type theory first and foremost, such that it has its specific
inference rules which also correspond to the internal language of an `inf`-topos. Furthermore, Homotopy Type Theory
often uses so-called cubical sets, as opposed to simplicial sets. Nevertheless, category theory, and specifically higher
category theory, can serve as a foundation for the concepts which underpin homotopy types.
