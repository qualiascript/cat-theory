# `cattheory.org`

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

This project is open source and hosted on GitHub Pages. You can find the repository
[here](https://github.com/qualiascript/cat-theory/). Issues and pull requests are welcome, however it is unlikely I
will accept large contributions, as to keep a consistent style throughout. 

## Table of Contents
### Section I: Essentials of Computation
1. [Categories](sections/1_essentials/01_categories.md) (+ Isomorphisms)
2. [Category of Categories](/sections/1_essentials/02_category_of_categories.md) (+ Functors)
3. [Homfunctors](sections/1_essentials/03_homfunctors.md) (+ Internal Homfunctors)
4. [Functor Categories](sections/1_essentials/04_functor_categories.md) (+ Natural Transformations)
5. [Currying and Uncurrying](sections/1_essentials/05_currying_uncurrying.md) (+ Adjunctions)
6. [Diagonal Functor](sections/1_essentials/06_diagonal_functor.md) (+ Limits, Colimits, Products, Coproducts)
7. [Cartesian Closed Categories](sections/1_essentials/07_cartesian_closed_categories.md) (+ Evaluation Map, Lambda Calculus)
8. [Presheaves](sections/1_essentials/08_presheaves.md) (+ Yoneda Embedding)
9. [Equalizers and Coequalizers](sections/1_essentials/09_equalizers_coequalizers.md) (+ Pullbacks, Pushouts)
10. [Algebras and Coalgebras](sections/1_essentials/10_algebras_coalgebras.md) (+ Catamorphisms, Anamorphisms)
11. [Monoids and Comonoids](sections/1_essentials/11_moniods_comonoids.md) (+ Monads, Comonads)
12. [Fixed Points](sections/1_essentials/12_fixed_points.md) (+ Fixed Point Combinator, Diagonal Arguments)

### Section II: Intuitionistic Computation
1. [Comma Categories](sections/2_intuitionistic/01_comma_categories.md) (+ Slice Category, Base Change Functor)
2. [Kan Extensions](sections/2_intuitionistic/02_kan_extensions.md) (+ Local Kan Extensions)