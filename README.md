# Learaning Haskell

## Haskell Overview

*Haskell* is named after American mathematician and logician Haskell Curry. At the core of the language is the principle that:

> A proof is a program; the formula it proves is a type for the program.
> - Haskell Curry

As a programming language, it showcases the following features:

+ Lazy evaluation
+ Pattern matching
+ List comprehension
+ Type classes
+ Type polymorphism

The language exhibits the following classifications:

+ Strong typing
  + The language is strict in the intermixing of data types
+ Static typing
  + Types for all variables are checked at compile time
+ Purity
  + In general, functions in Haskell do not have *side effects*
+ Functional
  + The function (not the object) is a first class citizen in Haskell

##  Why Haskell?

+ Exposes a different paradigm for programmers (learning it *will* make you a better programmer, in the same way that learning a foreign language improves your English grammar).
+ Excels in certain use cases:
  + High performance concurrency and parallelism
  + Highly complex code that needs to be easily maintainable and bug free
  + Rapid prototyping (while still having fast code)
  + Solving "functional" problems
+ Haskell is concise
+ If it compiles, it's probably correct
+ Laziness is free, can always strictify later easily
+ Integrates very well with other languages
+ Has an intelligent community and is well documented
+ Is extremely fun to program in
+ Can exercise your brain in ways you didn't think possible

## Basic Syntax

### Basic function definition

```haskell
add x y = x + y
```

```haskell
trueifone 1 = True
trueifone _ = False
```

### Pattern Matching

```haskell
quicksort [] = []
quicksort (p:xs) = (quicksort lesser) ++ [p] ++ (quicksort greater)
  where
    lesser = filter (< p) xs
    greater = filter (>=p) xs
```

### List Comprehension

```haskell
[ x*y | x <- [2,5,10], y <- [8,10,11], x*y > 50]
```
produces
```haskell
[55,80,100,110]
```

### Tuples

You can group mixed data types in a single piece of data as a tuple.

```haskell
area :: (Bool, Double) -> Double
area (True, x) = x * x
area (False, x) = 3.14159 * x * x
```

### Higher Order Functions

```haskell
takeThreeElements = take 3
```
The function `take` by itself usually takes two arguments: the number of elements to return and the list to take the elements from. By supplying one argument, we produce a function that accepts only one argument instead of two.

### Lambdas, Folds, Monads, Functors, and more ...

The constructions are fairly far reaching. Haskell is considered a "difficult" programming language to learn for this reason. However, these constructions are what make Haskell programs concise, correct, and expressive.

### Case study: Computing prime numbers

```haskell
primes :: [Integer]
primes = sieve [2..]
  where
    sieve (p:xs) = p : sieve [x|x <- xs, x `mod` p > 0]
```
[Literate Programming](http://en.literateprograms.org/Sieve_of_Eratosthenes_%28Haskell%29)

Wat.