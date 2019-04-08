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

This can be applied to methods:

```java
public <V> V process(final V input);
```

This example will force the input and output to be the same type.

```java
ModelObject input;
ModelObject output:

input = new ModelObject();
output= new ModelObject();

output = process(input);
```

## Concrete Generics

It is possible specifying more exactly the type used:

```java
public class WithGeneric<T>;

public class WithGeneric<T extends Number>;
```

It is even possible to define multiple inheritances:

```text
public class WithGeneric<T extends A & B & C>;
```

## Wildcards

If needed a wildcard generic type, which accepts any type, can be used:

```java
List<?> list;
```

### Inheritance

This is an upper bounds wildcard:

```java
List<? extends Number> list;
```

Which accepts Number and it subclasses.

This is an lower bounds wildcard:

```java
List<? super Number> list;
```

Which accepts Number and it super-classes.

## Type Erasure

Generics and types and checked at compile time. That means that they won't check types during runtime.

While this makes them more efficient it also means that types can be lost during runtime, and for example a list of Number may end containing Strings.

The erasure is a bit more complex than that, but it means that types should be set explicitly always to avoid problems.

## Type Parameter Naming Conventions

Use single upper-case letters.

The most commonly used type parameter names are:

* E - Element \(used extensively by the Java Collections Framework\)
* K - Key
* N - Number
* T - Type
* V - Value
* S,U,V etc., 2nd, 3rd, 4th types

## More Information

* [Generics](https://docs.oracle.com/javase/tutorial/java/generics/index.html)

