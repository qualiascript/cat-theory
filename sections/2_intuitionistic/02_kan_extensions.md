# II. 2. Kan Extensions

We would like to have a construction which represents the concept of universal property in categorical terms. The
commonality different universal properties have is that they are the best possible approximation of an action. Then,
we could conceptualize it as two functors, `F : C -> D` representing some action, and `P : C -> C'` which diverts
the action to some other category. We would like a formulaic method of obtaining the best possible `G : C' -> D`, so
that `P . G` acts as an approximation of `F`.

Recall that limits are right adjoint to the diagonal functor. The diagonal functor `Diag :: [C, C ^ D]` operates on
`c :: C` and creates a functor `Const d = c`. The constant functor can be conceptualized as the composition of two
functors, `P : D -> 1` and `C' : 1 -> C`, so that `C' 1 = c`. But `c :: C` is alternatively `C' : 1 -> C` which is
exactly the functor we need. Then, the diagonal functor is alternatively `Diag :: [[1, C], [D, C]]`, whose action
is to precompose the functor argument with `P`. Let us generalize this.

Any functor `P : C -> C'` induces a functor `P' :: [[C', D], [C, D]]` so that `P' X = P . X`. When `C' = 1`, this is
the diagonal functor, whose right adjoint defines limits and left adjoint defines colimits. Its action consists of
creating potential solutions `S :: [C, D]` given an apex `G : 1 -> D` by precomposing with `P : C -> 1`. By
generalizing, `P' :: [[C', D], [C, D]]` takes possible solutions to our original functor problem and precomposes them
so that they become approximations of `F : C -> D`.

Then, finding the best solution amounts to finding the terminal object in the comma category `P' \/ G`, for
`G :: [C', D]`, so that any other solution factorizes to it uniquely. Or, alternatively, finding the initial object of
`G \/ P'`, which factorizes to any other solution uniquely. Recall that this is the same as finding the right adjoint
and left adjoint functors respectively, which in the case of the diagonal functor, yield the limit and colimit functors.

Then, for any functor `P' :: [[C', D], [C, D]]` obtained by precomposing with `P : [C, C']`, the right adjoint is known
as the right Kan extension, and the left adjoin is known as the left Kan extension. They are denoted
`Ran P, Lan P :: [[C, D], [C', D]]` for the right and left version respectively. For some `F :: [C, D]`, we also denote
`Ran P F` as the right Kan extension of `F` along `P`, and `Lan P F` as the left Kan extension of `F` along `P`.

## Examples of Kan Extensions

We have seen that limits and colimits are instances of Kan extensions. In fact, so are representable presheaves.
The following is not yet a proof of that statement, but a demonstration of one connection between the two concepts.

The problem of showing `Pr` is representable is the same as finding the terminal object of `Yo \/ Pr`. Given the Yoneda
embedding `Yo :: [C, [op C, Set]]`, we wish to leave it unchanged, so that we have `id Yo` inducing the functor
`P' :: [[C, [op C, Set]], [C, [op C, Set]]]`. A morphism from `id Yo` to `F` is the same as a morphism from `Yo` to
`F`. Then the right Kan extension of `F`along `id Yo` is the terminal object of `Yo \/ F`, which exists if `F` is
representable. Thus `F` is representable if and only if `Ran (id Yo) F` exists.

However, this induces a problem: we have defined Kan extensions as functors, and in this case, `Ran (id Yo)` is not
defined over the entire domain of the functor. We can solve this by providing a definition of `Ran P F` specifically:
`Ran P F :: C' -> D` is the functor so that `hom(P' x, F) ~= hom(x, Ran P F)`, similarly for `Lan P F`. This is simply
applying the definition of the adjunction at a specific value `F`, so that the Kan extension is defined even if the 
full adjunction doesn't exist. This is known as the local Kan Extension, which we will be using going forward.

In fact, we have previously talked about limits and colimits of diagrams without necessarily defining the limit and
colimit functors, which is technically unfounded. However, since we have a concept for local Kan extensions, we can
transfer that to local products and coproducts. As such, this usage of products and coproducts was in fact correct.

We can also formulate the property of adjunctions `F -| G` in terms of Kan extensions. The right adjoint of `F : C -> D`
exists if `F \/ id C` has a terminal object, and is, in fact, isomorphic to that terminal object. By inverting the
comma category, we find that we must obtain the initial object of `id C \/ F`. This induces the constant functor
`P' :: [[C, C], [C, C]]`, and finding the initial object is the same as finding the left Kan extension. As such,
`G ~= Lan (id C) F`, and by analogy, `F ~= Ran(id D) G`. Note that the Kan extension and adjunction directions reverse!

## Kan Extensions as Natural Transformations

[TO BE CONTINUED]