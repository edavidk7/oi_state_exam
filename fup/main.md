# FUP

Status: Done

# Requirements

Funkcionální jazyky a jejich vlastnosti. Lambda kalkulus, iterativní konstrukty a rekurze.

• Čisté funkce (pure functions), jejich výhody a nevýhody.

• Rekurzivní funkce, typy rekurze, koncová rekurze (tail recursion).

• Reprezentace seznamů a stromů ve Scheme/Racketu.

• Víceřádové funkce (higher-order functions), příklady, currying a částečně vyhodnocené
funkce, levý a pravý fold.

• Funkční (neboli lexikální) uzávěry, příklady.

• Lambda kalkulus, alfa-konverze, beta-redukce, evaluační strategie (normal a applicative),
normální forma, Church-Rosserova věta, Y-combinator.

• Algebraické datove typy (ADT) v Haskellu, příklad rekurzivního ADT.

• Typové třídy (type classes) v Haskellu, polymorfismy v Haskellu.

• Typové třídy Functor, Applicative functor, Monad a jejich použití.

![image.png](assets/image.png)

# Pure functions

![image.png](assets/image%201.png)

They operate only on the input data, returning some different data, and have no persistent state or outside effects (side effects).

A pure functional program is a program composed only of pure functions.

## Advantages

Easy to debug, minimum amount of things that can go wrong (e.g. unit testing). 

Easy refactoring (all functionality is restricted to one place, don’t have to worry about the outside world)

Parallelization, concurrency (launch the function on multiple instances with no synchronization)

Formal verification of code correctness

Call caching

## Challenges

Cannot use loops, they need to mutate some state by definition

Instead, use recursion and hold the intermediate results on the system stack

Cannot change data structures → we must always create an altered copy → expensive

Typically less efficient that imperative/OOP (cannot cache, must copy etc.)

## Persistent Data Structures

![image.png](assets/image%202.png)

We only change the altered state (copy on write)

## Side Effects

If we had no side effects, FP programs would be useless (how do you return the result of the computation?)

![image.png](assets/image%203.png)

Try to separate it as best as possible

## Functional vs Imperative

![image.png](assets/image%204.png)

# Higher-order functions

Functions that operate on a function

![image.png](assets/image%205.png)

## List-wise HOF

![image.png](assets/image%206.png)

### Map

![image.png](assets/image%207.png)

### Folding

![image.png](assets/image%208.png)

## Currying

![image.png](assets/image%209.png)

We can split a multi-argument function into a series of functions that receive a single argument and return a function that returns the rest

![image.png](assets/image%2010.png)

## Function composition

![image.png](assets/image%2011.png)

### Point-free functions

All operations are composed into a single large function which then gets called on the argument.

## Closures

![image.png](assets/image%2012.png)

Similar to free variables in predicate logic

Closure definition:

![image.png](assets/image%2013.png)

### Binding scope

![image.png](assets/image%2014.png)

### Closure example

![image.png](assets/bd843472-924d-4696-b56e-2697307b6240.png)

# Recursion

![image.png](assets/image%2015.png)

### Linear

```python
f(x):
	y = f(x-1)
	result = y**2 + x
	return result
```

### Tail

```python
f(x):
	return f(5x-3)
```

### Tree

```python
f(x):
	y = f(x-1)
	z = f(2x-5)
	result = y**2 + x - z
	return result
```

Tail recursion has advantage of O(1) memory complexity, as the tail call can be eliminated (don’t need to store the previous’ call memory on the stack, can rewrite with the new call)

# Lisp-like languages

Lisp = list processor

We use Racket

A lot of brackets 

Uses a lot of brackets and prefix notation for operators

![image.png](assets/image%2016.png)

Evaluation strategy is innermost to outermost bracket, and is eager most of the time

Conditionals tend to be lazy

Example code:

![image.png](assets/image%2017.png)

## Pairs

![image.png](assets/image%2018.png)

Is a linked data structure, can be used to create a hierarchical data structure similar to a binary tree

Cons function (binary): create a new pair with 2 elements, if the second one is a list, it creates a new list

Car function: get the first element of a pair

Cdr function: get the last element of a pair

## Lists

![image.png](assets/image%2019.png)

Linked pairs

List function (n-ary): create a new list from the given arguments

If we want to compare, we may only use the eq? function (deep equality)

## Trees

Nested lists or pairs

![image.png](assets/image%2020.png)

## Lazy evaluation

![image.png](assets/image%2021.png)

### Thunking

![image.png](assets/image%2022.png)

## Streams

![image.png](assets/image%2023.png)

### Example

![image.png](assets/image%2024.png)

## Interpreters

![image.png](assets/image%2025.png)

Use the built-in interpreter of the language to parse our custom language, we just need the evaluator. 

Advantage is that the source code can be directly mapped to a tree structure.

# Pattern matching

Decompose a data structure to its components and branch the code (a switch statement on steroids).

![image.png](assets/image%2026.png)

# Lambda calculus

We restrict ourselves to untyped lambda calculus

![image.png](assets/image%2027.png)

## Syntax

![image.png](assets/image%2028.png)

Lambdas are left-associative, we drop the brackets.

![image.png](assets/image%2029.png)

Alpha conversion allows us to rename the bound variables arbitrarily. However, it must not name clash with another bound variable within the expression (a free variable would then become bound).

### Example

![image.png](assets/image%2030.png)

This is an AST of the lambda expression. V does not have a binding lambda, therefore it is a free variable in this expression

## $\beta$-reduction

The lambda term represents a function that can be applied to another expression

The application is performed by substitution for the variable bound in the lambda

![image.png](assets/image%2031.png)

## Examples

Simple single lambda substitution

![image.png](assets/image%2032.png)

Double substitution

![image.png](assets/image%2033.png)

Free argument

![image.png](assets/image%2034.png)

## Name conflicts

Again, we have to make sure that nothing in the argument (rightmost outermost) will become bound after substituting it into the lambda.

Eventual problems can be fixed using alpha conversion

![image.png](assets/image%2035.png)

Make sure to not propagate the substitution beyond the scope of the lambda expression (the binding lambda is the one closest in the AST).

## Evaluation strategies

![image.png](assets/image%2036.png)

![image.png](assets/image%2037.png)

Left: syntax tree inorder traversal.

![image.png](assets/image%2038.png)

## Computation in lambda calculus

Functions don’t have names, we apply a function by writing out its definition and the argument. Functions are only abbreviated using capital letters, but this abbreviation is **not part of the formal calculus**.

### Identity

![image.png](assets/image%2039.png)

### Booleans

![image.png](assets/image%2040.png)

Handy shortcut for an if statement

![image.png](assets/image%2041.png)

### Logical operators

![image.png](assets/image%2042.png)

Each takes two arguments

### Numbers

![image.png](assets/image%2043.png)

Functions of 2 variables, the number is encoded as the number of applications of $s$ to $z$

### Successor

+= 1 operator

![image.png](assets/image%2044.png)

![image.png](assets/image%2045.png)

We can use it for addition, by application successor to some N M-times

![image.png](assets/image%2046.png)

### Multiplication

Prefix-based, takes 2 arguments and calls the number N times on M

![image.png](assets/image%2047.png)

![image.png](assets/image%2048.png)

### Pair

![image.png](assets/image%2049.png)

### Y-combinator

![image.png](assets/image%2050.png)

Similar to the infinite loop, except we can apply an additional function to the arguments before looping. The left term in the duplication performs the recursion by repeatedly calling the target function.

# Haskell

## Basics

![image.png](assets/image%2051.png)

Both interpreted and compiled

## Basic data types

![image.png](assets/image%2052.png)

## Code example

![image.png](assets/image%2053.png)

Pattern matching directly in function definition

![image.png](assets/image%2054.png)

Where or let define a block, denoted by a pivot column in the code source file

## Conditions

![image.png](assets/image%2055.png)

Or using guards

![image.png](assets/image%2056.png)

## Lists

![image.png](assets/image%2057.png)

## Tuples

![image.png](assets/image%2058.png)

## List access patterns

There specific patterns that allow us to decompose lists and tuples by individual elements

![image.png](assets/image%2059.png)

## Type system

Haskell is strongly, statically typed

Strong: no automatic conversions or implicit casting (python style)

Statically: compile-time checks

![image.png](assets/image%2060.png)

### Function typing

![image.png](assets/image%2061.png)

Functions are automatically curried

### Polymorphism

Haskell allows polymorphic functions

![image.png](assets/image%2062.png)

![image.png](assets/image%2063.png)

Here, $a$ is the type variable. This makes the function fully parametrically polymorphic

For ad hoc polymorphism, we need type classes

### Type classes

![image.png](assets/image%2064.png)

The class defines methods that are defined for this type class

![image.png](assets/image%2065.png)

### Type declaration

![image.png](assets/image%2066.png)

They can be composed/nested, but not recursive

```haskell
type Trans = Pos -> Pos
```

### Algebraic data types

There are also algebraic data types, that are defined as a new type of data using a type constructor with individual data constructors

![image.png](assets/344042bb-ed83-4c1c-a069-1dc25cabab85.png)

They can be parametrized by other types

![image.png](assets/image%2067.png)

The most common is Maybe

```haskell
data Maybe a = Nothing | Just a
```

They can be defined recursively

![image.png](assets/image%2068.png)

### Records

![image.png](assets/image%2069.png)

### Type class

To make our custom datatype an instance of an existing type class (e.g. Eq), we implement the instance. The Show a ⇒ part says that we assume a is already an instance of show. If more assumptions are needed, write them in brackets (Show a, Ord a)

![image.png](assets/image%2070.png)

we can also define custom type classes

![image.png](assets/image%2071.png)

### Type class hierarchy

![image.png](assets/image%2072.png)

### Kinds

![image.png](assets/5dcc0147-0b00-4df9-be2d-bee1fcc7ccd2.png)

### Functor

Functor is a type class that defines types over which we can map

![image.png](assets/image%2073.png)

If we have a haskell list, fmap is equal to map. 

Example:

![image.png](assets/image%2074.png)

### Monad

![image.png](assets/image%2075.png)

The monad holds some computational context. The operations can be described as follows:

1. Take a structure $m$ of $a$, a function that transforms $a$ to $m$ of $b$, process and return $m$ of $b$
2. Replace the contents of $m$ with $b$
3. Wrap raw value into the context

Every monad is a functor:  

```haskell
fmap f x = x >>= return . f
```

Explanation: extract the variable in context, apply the raw function, and return a new context

To chain operations, we can use a do block

![image.png](assets/image%2076.png)

### Example: failing computations

![image.png](assets/image%2077.png)

A problem: when we want to apply a function that just takes an Int, it won’t work because we have a type Maybe Int

We can solve it using a functor

![image.png](assets/image%2078.png)

However, we still have a problem: it is difficult to compose operations that use Maybe. Solve it using the monadic composition

![image.png](assets/image%2079.png)

### Applicative Functor

Enable lifting of a binary operator similar to Functor

![image.png](assets/image%2080.png)

### State Monad

Need to solve the problem of stateful programming in Haskell

![image.png](assets/image%2081.png)

In FP, we must pack the state along with the computation variables. We can do it cleverly using a state monad.

![image.png](assets/image%2082.png)

The contents of this type are a function that maps the state to a new value and a new state.

![image.png](assets/image%2083.png)

### Foldable

Convenient for list aggregation

![image.png](assets/image%2084.png)

We can split the aggregation and traversing logic

![image.png](assets/image%2085.png)

![image.png](assets/image%2086.png)

![image.png](assets/image%2087.png)

Finally, we can use foldMap on Foldable instances

![image.png](assets/image%2088.png)

## I/O

Cannot avoid mutation of the state (outside world)

A naive solution is to use a World instance and pass it around

![image.png](assets/image%2089.png)

Doesn’t work well. We use Monads instead. This is the IO monad.

![image.png](assets/image%2090.png)

It is extensible

![image.png](assets/image%2091.png)