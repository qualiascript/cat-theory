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

[TO BE CONTINUED]