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

## Default Methods

These interfaces mix well with default methods, and the functional interfaces included in the JDK make use of them.

