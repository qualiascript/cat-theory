# II.3. Base Changes

Given a bundle `B : C -> D`, consider what it means for another bundle `A : D -> C` to be its right inverse, that is,
`A . B = id D`. `A` must map each `d :: D` to some value `c :: C`, and we know that `c` is mapped to `d` when `c` is
part of `B`'s fiber at `D`. Then, `d . A . B = d` suggests that the effect of `A` at `d` ought to be to map it to a
value so that it gets mapped back to `d`. Then, `A` must map each `d` to an element of the fiber of `B` at `d`. `A` is
known as a section of a bundle.

One may have morphism that reverses the effect of a bundle only at specific values, and it is undefined outside of that
range. By computing the pullback of two bundles `B : C -> D`, `F : E -> D`, one obtains a morphism `p : Pb(B, F) -> C`.
This operation obtains a fiber of the bundle for each of the fibers of `F`, and as such pullbacks are also known as
fiber products. By composing `H = p . B`, one obtains a new bundle whose action is only defined for some `c :: C`.
This restricted bundle can also have sections, in which case, they are referred to as local sections.

## Base Change Functor

The objects in the slice category `C / Y` are generalized elements of `Y`. Any two such elements, `k : K -> Y`, 
`x : X -> Y`, naturally induce a pullback, `Pb(k, x)` along with two projections `p : Pb(x, k) -> X` and
`p' : Pb(x, k) -> K`. Notice that these morphisms no longer live in `C / Y`, but in `C / X` and `C / K` respectively.
By focusing on `k` and taking it as any `p :: C / Y`, it implies that any morphism `x : X -> Y` in a category `C / Y`
induces a mapping of any `k` to a value of `C / K`. In fact, any `x` induces a functor, known as a base change functor.

The base change functor `BC_x : C / Y -> C / X` induced by morphism `x : X -> Y` maps each `k : K -> Y` to
`k' : Pb(x, k) -> X`, where `Pb(x, k)` can be conceptualized as fiber product: values that are part of the same fiber
in both `x` and `k`. For instance, if `double : FinSet -> FinSet`, `double a = 2 * a`, `size : List FinSet -> FinSet`
with `size` obtaining the size of the list, `BC_double size : List FinSet -> FinSet` only contains lists whose number
of elements is even. This demonstrates the effect of the base change functor in restricting generalized objects.

A type indexed by a value, which is simply a bundle in categorical terms, is known as a dependent type. In alternative
notation, we could denote `Vec UInt n` the dependent type which consists of a vector (that is, list), of unsigned
integers (that is, objects in `FinSet`) of size `n`. Then, the application of the base change functor amounts to
substituting `n` for `2 * n` to obtain `Vec UInt (2 * n)`, which are of size `2 * n` for some value `n`. In general,
a base change functor applied to a dependent type corresponds to a substitution.

## Dependent Products

Dependent products are the right adjoint of a base change functor. It is denoted as `DP_g`, where `g : X -> Y` is
the morphism that induced the base change functor. Hence, we have `hom_{C / X}(BC_g A, B) ~= hom_{C / Y}(A, DP_g B)`.
On the left side, a morphism between `BC_g A: Pb(A, g) -> X` and `A : a -> X` is given by a morphism
`f : Pb(A, g) -> b` so that `f . B = BC_g A`. On the right side, a morphism between `DP_g : R -> Y` and `B : b -> Y` is
given by a morphism `f' : A -> b` so that `f' . (DP_g B) = A`.

Consider the action of `BC_g A`: it maps pairs of elements `(x, a') : 1 -> X * A'` to just `x`. The elements have the
property that `x . g = a' . A`, so let us denote `q = a' . A`. Then, `f : Pb(A, g) -> a` sends `(x, a')` to some value
`e : 1 -> b` so that `e . B = (x, a') . (BC_g A) = x`. In other words, for each `q` so that `x . g = q`, `f` maps each
`x` in the fiber to an element of the fiber of `B` at `x`. As this is an adjunction, this respects the universal
property, meaning the left side is isomorphic to all such valid mappings.

Notice that this is almost the same as saying that for each fiber of `g`, the left side is the family of mappings for
each element of the fiber `x` to an element of `B` at fiber `x`. However, we have that `q = a' . A`, which limits
the construction only to some fibers of `g`, as induced by `A`. Also notice that selecting elements of the fiber of `B`
at every `x` in a fiber is the same as a local section of `B`. Thus, the left side is isomorphic to a family of local
sections of `B` for each fiber of `g` selected by `A`.

Then consider the left side, `hom(A, DP_g B)`, which is isomorphic to such a family of local sections. By setting
`A = id Y`, we get that `hom(id Y, DP_g B)` is the family of morphisms `f'` so that `f' . (DP_g B) = id Y`. This is
the sections of `DP_g B`! Then, each section of `DP_g B` is isomorphic to a family of local sections of `B` for each
fiber of `g`. Thus, `DP_g B : R -> Y` is a mapping of the local sections of `B` induced by the fibers of `g`, down to
the specific fiber which induced the section. Conveniently, this is also a dependent type.

## Dependent Sums

Dependent sums, denoted `DS`, are the left adjoint of the base change functor, `hom(DS_g A, B) ~= hom(A, BC_g B)`.
On the right side, we have the family of morphisms `f : a -> Pb(B, g)` so that `f . (Bc_g B) = A`. `f` maps each
`a' : 1 -> a` to some pair `(x, b') :: X * B`, with the property that `x . g = b' . B`. Then for each `a'` we have
`a' . f . (BC_g B) = a' . A`, in other words `x = a' . A`, meaning `a' . A . g = b' . B`. Then, `hom(DS_g A, B)` is
a family of morphisms that sends each `a' :: A` to some `b' :: B` so that `a' . A . g = b' . B`.

On the right side, let us set `A = id Y`. Then we have `hom(DS_g, id Y)` is a family of morphisms `f' : a -> Y` so that
`f' . (id Y) = DS_g A`. There is only one such morphism, and it is exactly `DS_g A`. Then, `DS_g A` is a morphism
that sends each `a' :: A` to some `b'` so that `a' . A . g = b' . (id Y)`. In other words, `DS_g A` sends each
`a' :: A` to `a' . A . g`. To put it simply, for any `A :: C / X`, `g : X -> Y`, `DS_g A = A . g`. Taken as
`DS_g A : R -> Y`, it simply corresponds to the elements `a :: a'` indexed by what fiber `A . g` sends them to.

## Dependent Products and Sums Intuition

Let us return to our previous example `Vec UInt n`. By applying the base change with `g : FinSet * FinSet -> FinSet`,
`g a b = a + b`, we obtain `Vec UInt (a + b) : List FinSet -> FinSet * FinSet`. Applying the dependent sum functor
`DS_g (Vec UInt (a + B))` undoes this reindexing, yielding back `Vec UInt n`. One could also compose with a morphism
such as `g' : FinSet * FinSet -> FinSet`, `g a b = a * b`, which indexes vectors by the product of the integers
whose sum index its size. Dependent sums yield function types that are inhabited when the original bundle is inhabited.

Consider the functor category `X = [(Vec UInt a) * (Vec UInt b), Vec UInt (a + b)]`. By itself, this does not impose a
consistency condition, however, consider a bundle `B : X -> FinSet * Finset` so that `X` is an internal homset of the
slice category. Then, given `g : FinSet * FinSet -> 1`, as `g` has one fiber, `DP_g B` is the family of sections of `B`.
As `X` comprises morphisms, it is the family of morphisms `m : (Vec UInt a) * (Vec UInt b), Vec UInt (a + b)` that 
respect consistency. As such, dependent products generalize homsets within slice categories.

In fact, for `g' : FinSet * FinSet -> FinSet`, `g' a b = a * b`, consider `DP_g' B`. The fibers of `g'` consist of
values `n :: FinSet` so that `a * b = n`, and for each such fiber, the same family of morphisms is constructed. As
such, it is a family of morphisms `m : (Vec a) * (Vec b) -> Vec (a + b)` for each `n :: FinSet` so that `a * b = n`.
Then, given an `n`, a morphism that inhabits the dependent product is imposed with an extra condition. The dependent
product at each fiber is inhabited if there is at least one morphism for any given values following some condition.

In fact, by the Curry-Howard-Lambek correspondence, dependent types are additionally propositions that depend on values.
The fiber at some value could be uninhabited, meaning the proposition is false at that value, or be inhabited by
multiple proofs of the proposition at the value. As we will soon see, dependent products are a categorification of the
universal quantifier, and dependent sums for existential quantifiers. As such, they are elementary building blocks
in providing a categorical model whose inner logic corresponds to mathematical proofs.