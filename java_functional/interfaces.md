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

## 

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



