---
title: Functional Programming in C# why should I care❓❓
---
## What is Functional Programming
Purity/Pure Functions or referentially transparent - a function always produces the same result if you supply it with the same arguments. We shouldn't mutate an existing type that we receive in the function; it's better to return a new one. 
 Expressions instead of statements - shorter lines of code easier to read;
Method Chaining and extension method - best thing ever :-)
Declarative programming instead of imperative programming using LINQ - much more simple to read
Immutable Collections and types - collections that cannot change since it is created.
## Advantages?
	The code becomes clearer because we use a declarative approach and method signature honesty. With pure functions, we know exactly where the source of change is. We know precisely what to count with. 
We don't need to worry about mocking dependencies to build unit tests with pure functions. 
## Disadvantages?
 -Curve line to learn how to apply it. Can I apply to an existing project??
- Using immutable values and recursion can lead to more memory consumption.
- Working with immutable states and objects we cannot change it, and we have to create a new one always. Such extra work...

## Where do you change the state?
	We need to mutate the state at some point. We need to do it in the repository layer since it is dealing with an IO operation what means that he has no control over the return.

## Sources of dishonesty:
Exceptions;
Side effects not described in the method name and returns;
Primitive Obsession