---
description: Java Generics
---

# Generics

Generics allow templating classes to specify types.

This is a list without generics:

```java
List list = new ArrayList();
list.add("hello");
String s = (String) list.get(0);
```

This is the same list, specifying it contains Strings:

```java
List<String> list = new ArrayList<String>();
list.add("hello");
String s = list.get(0); // no cast
```

### Diamond Operator

Since Java 7 the type can be implicit:

```java
List<String> list = new ArrayList<>();
```

## Generic Methods

This can be applied  to methods:

```java
public <V> V process(final V input);
```

This example will force the input and output to be the same type.

## Concrete Generics

It is possible specifying more exactly the type used:

```java
public class WithGeneric<T>;

public class WithGeneric<T extends Number>;
```

It is even possible to define multiple inheritances:

```
public class WithGeneric<T extends A & B & C>;
```

## Type Parameter Naming Conventions

Use single upper-case letters.

The most commonly used type parameter names are:

*  E - Element \(used extensively by the Java Collections Framework\)
* K - Key
* N - Number
* T - Type
* V - Value
* S,U,V etc., 2nd, 3rd, 4th types

## More Information

* [Generics](https://docs.oracle.com/javase/tutorial/java/generics/index.html)



