# II.4. Locally Cartesian Closed Categories

Previously, we have assumed that a given slice category `C / x` has products and internal homsets. This is not
immediately given. Let us define a Locally Cartesian Closed Category (henceforth a LCCC) to be a category `C :: Cat`
with a terminal object so that every slice category `C / x` for `c :: Cat` is a CCC. Then, `C / 1 = C` is also a CCC,
so that any LCCC is a CCC. Just like CCCs have their internal logic be equivalent to simply typed lambda calculus,
LCCCs provide a model for dependently typed programming languages, although not the strongest one.

