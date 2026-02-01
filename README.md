## Title of Contents
1. [Categories](chapters/001_categories.md) (+ Isomorphisms)
2. [Category of Categories](/chapters/002_category_of_categories.md) (+ Functors)
3. [Homfunctors](chapters/003_homfunctors.md) (+ Internal Homfunctors)
4. [Functor Categories](chapters/004_functor_categories.md) (+ Natural Transformations)
5. [Currying and Uncurrying](chapters/005_currying_uncurrying.md) (+ Adjunctions)
6. [Diagonal Functor](chapters/006_diagonal_functor.md) (+ Limits, Colimits, Products, Coproducts)
7. [Cartesian Closed Categories](chapters/007_cartesian_closed_categories.md) (+ Evaluation Map, Lambda Calculus)
8. [Presheaves](chapters/008_presheaves.md) (+ Yoneda Embedding)
9. [Equalizers and Coequalizers](chapters/009_equalizers_coequalizers.md) (+ Pullbacks, Pushouts)
10. [Algebras and Coalgebras](chapters/010_algebras_coalgebras.md) (+ Catamorphisms, Anamorphisms)
11. [Monoids and Comonoids](chapters/011_moniods_comonoids.md) (+ Monads, Comonads)
12. [Fixed Points](chapters/012_fixed_points.md) (+ Fixed Point Combinator, Diagonal Arguments)

## What is this?

`cattheory.org` is a guide to category theory, especially from a computational perspective. Category theory is the
study of mathematical structures, focused on relations between mathematical objects as opposed to the inner content of
the objects themselves. This is formalized into categories, which include objects, treated as black boxes, and
composable relations between objects known as morphisms. The so-called categorical perspective does not lose any
information compared to traditional mathematics. It can be seen as a generalization of set theory and abstract algebra.

This guide presupposes some basic knowledge of set theory (sets, functions, Cartesian products, injections, 
surjections, bijections), and some familiarity with graph theory helps to visualize the categories. Additionally,
familiarity with functional programming will make concepts more intuitive, however the guide can also serve as an
introduction to the functional paradigm. While prerequisites are low, this guide is not easy. The writing is clear
but dense, and it is recommended to pay attention to each sentence and re-read parts if necessary.

The motivation for this guide lies in bridging the gap between computation and mathematics. Category theory, in many
ways, acts as a sort of programming language of math itself. Many resources online use a more mathematical style
of notation and writing, which can hinder that intuition. On the other hand, other resources rely too much on
intuition, which is detrimental as the abstraction layers increase. Furthermore, this guide derives concepts whenever
possible, as to illustrate the motivation behind mathematical concepts beyond the formal definitions.