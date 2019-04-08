---
description: Inheritance in Java
---

# Inheritance

There are two ways to handle object inheritance in Java: interfaces and abstract classes.

## Abstract Classes

The easiest way is using abstract classes, but each class can inherit from a single abstract. On the other hand an abstract class can contain code.

## Interfaces

Any class can inherit from many interfaces, but these contain no code. Instead they offer a common set of methods for the class.

It is recommended using an interface before an abstract class, as this will decouple code from more specific implementations.

### Constants in Interfaces

Avoid adding constants to interfaces.

### Interfaces and Testing

By using interfaces the code can be made easier to test, as implementations can be swapped with few problems.

### Interfaces and Dependency Injection

In a similar way to testing, interfaces make it easier injecting dependencies, and swapping them.

## Checking Inheritance

```java
object instanceof ClassName
```

```text
ClassName.class.isAssignableFrom(object)
```

## More Information

* [Interfaces and Inheritance](https://docs.oracle.com/javase/tutorial/java/IandI/index.html)

