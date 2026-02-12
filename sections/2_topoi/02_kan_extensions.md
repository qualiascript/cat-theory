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

## Adjunctions as Kan Extensions

We can also formulate the property of adjunctions `F -| G` in terms of Kan extensions. The right adjoint of `F : C -> D`
is isomorphic to the terminal object of `F \/ id C`. By inverting the comma category, we find that we must obtain the
initial object of `id C \/ F`. Let `F` induce `P' : [C, C] -> [D, C]`. Then we have `id C \/ F ~= id C \/ P' (id C)`.
So the left adjoint of `P'` specifically at value `id C` is isomorphic to the left adjoint of `F`. As such,
`G ~= Lan F (id C)`, and by analogy, `F ~= Ran G (id D)`. Note that the directions mirror the adjunction's.

However, this induces a problem: we have defined Kan extensions as functors, and in this case, `Lan (id C)` is not
defined over the entire domain of the functor. We can solve this by providing a definition of `Ran P F` specifically:
`Ran P F :: C' -> D` is the functor so that `hom(P' x, F) ~= hom(x, Ran P F)`, similarly for `Lan P F`. This is simply
applying the definition of the adjunction at a specific value `F`, so that the Kan extension is defined even if the 
full adjunction doesn't exist. This is known as the local Kan Extension, which we will be using going forward.

In fact, we have previously talked about limits and colimits of diagrams without necessarily defining the limit and
colimit functors, which is technically unfounded. However, since we have a concept for local Kan extensions, we can
transfer that to local limits and colimits. As such, this usage of limits and colimits was in fact correct.

## Representable Presheaves as Kan Extensions

Consider `Lan A 1'` for `A : C -> C`, `A x = a`, `1' : C -> Set`, `1' x = 1`. Then the induced functor is
`P' :: [[C, Set], [C, Set]]`, `P' X = H` so that `H p = X a`. Then we have `hom(Lan A 1', y) ~= hom(1', P' y)`. Then
in `op C`, `hom(P' y, 1') ~= hom(y, Lan A 1')`. Let us set `y = Yo b`, then `hom(Yo b, Lan A 1') ~= Lan A 1' b` and
`hom(P' (Yo b), 1') ~= hom(Yo b a, 1') ~= hom(a, b)`. Then, `Lan A 1' b ~= hom(a, b)`. Thus, representable presheaves
are the left Kan extensions of `1'` along the constant functor corresponding to the object in question.

Intuitively, `1' :: [C, Set]` seeks to map any `b :: C` to the singleton set, but its path is diverted to `a`, so it
seeks to return to `b`, and since it is the left version, it finds all solutions `hom(a, b)`. Limits, colimits, 
adjunctions and representable presheaves all turn out to be Kan extensions, and as such, the concept does genuinely
capture the idea of universal constructions. In this regard, Kan extensions hold a special role in category theory,
as all concepts that rely on the idea of a "best solution" can be defined as mere instances of the general pattern.

## Kan Extensions as Natural Transformations

Note that when defining local Kan extensions, we gave the formula `hom(P' x, F) ~= hom(x, Ran P F)`. As the categories
of the homset are functors, this is a statement about natural transformation. The adjunction `P' -| Ran P`, defined
locally at `F`, suggests that `Ran P F` is the terminal object in `P' \/ id F`. This induces the natural transformation
`a : P' (Ran P F) -> F`, so `a : (Ran P F) P -> F`. which is terminal, so that any other `a' : G P -> F` factors
uniquely to it. Similarly, the natural transformation `b : F -> (Lan P F) P` is initial.

This suggests another definition for Kan extensions: the right Kan extension is a functor `Ran P F` along with a
natural transformation `a : (Ran P F) P -> F` which is terminal in `G P \/ F` for any `G`. The left Kan extension is a
functor `Lan P F` along with a natural transformation `b : F -> (Lan P F) P` which is terminal in `F \/ G P` for any
`G`. This demonstrates the sense in which Kan Extensions find the best solution, from the left or from the right,
to the problem of reconstructing `F` after it's been diverted through `P`.