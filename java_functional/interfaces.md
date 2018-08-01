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

## 

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



