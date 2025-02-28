---
title: Functions vs Methods
date: 2024-10-12 14:27:29
tags: ["Scala"]
---
## difference

What is the difference between the following definitions of increment?

```scala
def increment(x: Int): Int = x + 1
val increment: Int => Int = x => x + 1
```

In both cases, we can call increment like the following:

```scala
increment(41) // : Int = 42
```

A key difference is that the second version defines a value that can be
passed as a parameter or returned as a result.

The runtime creates an object for it in memory.

## apply method

```scala
val increment: Int => Int = x => x + 1
```

Calling a function means calling its method apply:

```scala
increment(41)
// is equivalent to
increment.apply(41)
```

When we write increment(41), the compiler rewrites it to
increment.apply(41).

## convert automatically

Most of the time, you don’t need to think about whether you use a
method or a function, because the compiler is able to automatically
convert methods into functions, when necessary.

For instance, you can write:

```scala
val xs: List[Int] = List(1, 2, 3)
def increment(x: Int): Int = x + 1
xs.map(increment) // = List(2, 3, 4)
```

Here, the compiler sees that the operation map expects a function, so it
converts the method increment into a function value.
