# Chapter 2: Category of Categories

It is a natural next step to consider what a category of categories would entail. Let us name the category of all
categories `Cat`. Clearly, its objects ought to be categories, but it is not immediately apparent what its
morphisms ought to be.

Recall that categories are defined by an object set and a set of morphisms (henceforth a homset). One idea could be that
a morphism between objects in a category of categories is defined as a pair of functions, one between object sets and
one between homsets. 

However, this definition is flawed. It would imply that any two categories with the same cardinality of objects and
homsets are isomorphic, which is practically untrue due to the different configuration of morphisms encoding different
categories. That is, categories have extra structure when compared to sets, and morphisms in `Cat` ought to respect it.

These morphisms will still consist of a pair of functions, one between object sets and one between homsets. However,
not all such pair of functions will make for a valid morphism in `Cat`.

## Functors

Morphisms respect composition. This must also be true for morphisms in `Cat`, which we will henceforth be referring to
as functors. As such, we can immediately derive some laws any eventual definition of functors must follow:
- Functors ought to compose, that is, if `F : A -> B`, `G : B -> C` then `F . G : A -> C`
- There ought to be an identity functor for any category `A`, so that `id A . F = F`, `G . id A = G`
- Functor composition is associative. That is, `(F . G) . H = F . (G . H)`

Practically speaking, the identity functor maps each object and morphism of a category to itself.
This is because, for any functor `F` and any object or morphism `x`, we have `F x = ((id A) . F) x = F((id A) x)`.

We would like for functors to respect the composition structure of the underlying categories. That is the structure that
categories exist to model in the first place. As such, we impose the following additional rule:
- Functor application on morphism composition is distributive. That is, `F (f . g) = F f . F g`

We observe this is trivially true for `(id A)(f . g) = f . g = ((id A) f) . ((id A) g)`. As such, identity functors
already respect the distributive law. And as we have conceptualized functors as a pair of functions, it is clear that
composition and associativity also hold. 

## What is the intuition behind functors?

Once again, a functor is defined as simply being a morphism in `Cat`, that respects the laws above. It is important to
remember that intuitions are built on top of formal definitions, not the other way around.

Categories act as generalizations of sets. By extension, functors are in `Cat` what functions are in `Set`. This is
distinct from morphisms, which are equivalent to a function *within* the context of a specific category. Functors are
functions *between* two categories.

Looking specifically at the effect of functor on object sets, they may collapse multiple objects in the domain into
the same object in the codomain. There may also be objects in the codomain which are not reached. As such, a functor
will embed a category within a subset of another category's objects, potentially merging objects in the process.

However, the distributive property means that following a path in the original category's graph and then applying the
functor is the same as applying the functor to each individual morphism. In other words, if we have a functor
`F : A -> B`, we don't need to be concerned of `B`'s specificities, and we can still operate as if we are in `A`.

## Other types of functors

An endomorphism is any morphism in a category from an object to itself. By extension, an endofunctor is a functor from
a category to itself, i.e., `F : C -> C`. It can be envisioned as applying some sort of category-internal operation.

If a functor corresponds to an isomorphism within `Cat`, the two categories which the functor operates on are said to
be isomorphic. 

## Examples of functors

For any category `C`, there is a unique functor from `C` to `1`. It maps all objects of `C` to the singleton object,
and all morphisms to the singleton object's identity morphism. In other words, it forgets everything there is to know
about `C`. Trivially, it respects the distributivity law.

There is a diagonal functor `D : FinSet -> FinSet * FinSet`, which maps each natural number to a pair of numbers[^1]
using the formula `x -> (x, x)`. Notice that not all objects in the codomain category are reachable, as there is no
object in `FinSet` that would result in `(1, 2)`. Also notice that any operation that can be done with an `x` can be
immediately and losslessly transferred to `(x, x)`. This is the fundamental property of functors in action.

There is a functor between the preorder `(N, <=)` and `(R, <=)`, which simply maps every natural number to its real
number equivalent. It can be trivially seen that if two numbers are in a `<=` relation within the natural numbers,
they also are within the real numbers. As the objects and morphisms are simply embedded in a larger category,
`(N, <=)` is a subcategory of `(R, <=)`, and the functor is called an inclusion functor.

The oppositization functor `op` operates on any category `C` and returns its opposite category, denoted `op C`.
The opposite of a category is the category where every morphism from `A` to `B` in the original category becomes
a morphism from `B` to `A`, and there are no other morphisms. In other words, it is the category whose underlying
directed multigraph is the transpose of the original category's directed multigraph. Furthermore, `op op C = C`

[^1]: Specifically, in `FinSet * FinSet`, the elements are within the Cartesian product `N * N`, where `N` is the natural numbers. Products will be explored in more detail later on.
