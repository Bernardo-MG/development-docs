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
protected abstract Iterable<T> onRead(final T sample);

protected final <I, O> Iterable<O> read(final I sample, final Function<I, O> strategy)
{
   return strategy.apply(sample);
}

public final read(final I sample) {
   return read(input, this::onRead);
}
```

## Predicate

A logical predicate, which can be combined with or and and operations, or negated.

## Consumer

Takes an argument, but returns nothing. Used for operations with side effects.

## Supplier

Receives no argument but returns an object. Can be used as a strategy for initialization.

```java
Supplier<Entity> supplier;

supplier = Entity::new;

// Both lines create a new entity
Entity ent1 = new Entity();
Entity ent2 = supplier.get();
```



