---
description: Java Functional Interfaces
---

# Interfaces

Functional interfaces only have a single method.

They can be annotated with @FunctionalInterface to ensure, during compile, that they fit this requirement. If the marked interface gets more than one method then it won't compile.

```java
@FunctionalInterface
public interface Function<T, R>
```

These interfaces are very useful when working with the functional paradigm, as with them it is easy making sure that operations have a single concern.

By default Java comes with several functional patterns.

## Function

The Function interface can encapsulate an operation, and allows chaining functions by using the compose and andThen methods.

```java
Function<String, Integer> function;
Integer result;

// Function initialization is skipped

result = function.apply("abc");
```

### Chaining Functions

The interface contains default methods to chain operations through function composition:

```java
Function<String, Integer> function1;
Function<Integer, String> function2;
Function<Integer, String> firstThenSecond;
Function<Integer, String> secondThenFirst;

// Function initialization is skipped

// Apply function 1 then function 2
firstThenSecond= function1.andThen(function2);

// Apply function 2 then function 1
secondThenFirst = function1.compose(function2);
```

### Mapping Methods

Any method can be used as a function.

In this case an abstract method will be used as a strategy, to support the template method pattern. This method is as follows:

```java
protected abstract Iterable<T> onRead(final T sample);
```

Then we have another method ready to make use of a function with the same erasure:

```java
private final <I, O> Iterable<O> read(final I sample, final Function<I, O> strategy)
{
   // Additional operations goes here
   return strategy.apply(sample);
}
```

And now this can be used like this:

```java
public final read(final I sample) {
   return read(input, this::onRead);
}
```

While at first this may be overly complex, take not that in a real application the second method would encapsulate complex operations, allowing the programmer to just change the particulars of the read operation:

```java
public final read1(final I sample) {
   return read(input, this::onRead1);
}

public final read2(final I sample) {
   return read(input, this::onRead2);
}

public final read3(final I sample) {
   return read(input, this::onRead3);
}
```

### Extensions

The JDK includes a BiFunction, which supports two arguments as input, and a few extensions for numeric primitives, and a binary operator which takes two instances of the same type.

## Predicate

A logical predicate, which can be combined with or and and operations, or negated.

```java
Predicate<Integer> predicate;
Boolean result;

// Predicate initialization is skipped

result = predicate.test(12);
```

### Logical Operations

The interface contains default methods for boolean operations:

```java
Predicate<Integer> predicate1;
Predicate<Integer> predicate2;
Predicate<Integer> alwaysTrue;
Predicate<Integer> alwaysFalse;
Predicate<Integer> both;
Predicate<Integer> one;

// Predicate initialization is skipped

// True if both are true
both = predicate1.and(predicate2);

// True if one is true
one = predicate1.or(predicate2);

// Reversed
alwaysFalse = alwaysTrue.negate();
```

### Extensions

Just like with functions there is a BiPredicate and a few extensions for numeric primitives.

## Consumer

Takes an argument, but returns nothing. Used for operations with side effects.

```java
Consumer<String> consumer;

// Consumer initialization is skipped

consumer.accept("abc");
```

### Chaining Consumers

The default operations allow combining consumers:

```java
Consumer<String> consumer1;
Consumer<String> consumer2;
Consumer<String> firstThenSecond;

// Consumer initialization is skipped

// Apply consumer 1 then consumer 2
firstThenSecond = consumer1.andThen(consumer2);
```

## Supplier

Receives no argument but returns an object. Can be used as a strategy for initialization.

```java
Supplier<String> supplier;
String result;

// Supplier initialization is skipped

result = supplier.get();
```

## Mapping Constructors

Suppliers can be created from default constructors easily:

```java
Supplier<Entity> supplier;

supplier = Entity::new;

// Both lines create a new entity the same way
Entity ent1 = new Entity();
Entity ent2 = supplier.get();
```



