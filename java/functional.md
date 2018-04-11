---
description: Functional Programming in Java
---

# Functional Programming

Java 8 gave support to the functional programming paradigm in Java.

Several patterns are supported, such as pipelines \(as streams\), functions or mapping.

As usual with functional programming, try to keep functions pure. Keep the code in each component self-contained, and with no side effects.

## Functional Interface

Functional interfaces, marked with the @FunctionalInterface annotation, are single method interfaces. These are very useful when working with the functional paradigm, as it is easy to ensure they will have a single concern.

```java
@FunctionalInterface
public interface Function<T, R>
```

While any interface with a single method is a functional interface, which can be initialized from a lambda, those annotated will be checked during compilation, and cause an error if they don't meet the criteria for functional interfaces.

### Function

The Function interface allows chaining functions by using the compose and andThen methods.

### Predicate

A logical predicate, which can be combined with or and and operations, or negated.

### Consumer

Takes an argument, but returns nothing. Used for operations with side effects.

### Supplier

Receives no argument but returns an object. Can be used for initialization.

## Method References

Now methods can be passed as arguments in functions. These are not actual method references, but more an auto mapping feature, which transforms methods into an interface implementation.

Having these methods, which are both in the same class:

```java
public final <I, O> O read(final I sample, final Function<I, O> strategy);

protected <I, O> O onRead(final I sample){
   // This would encapsulate the code
}
```

It is possible using onRead as the operation strategy:

```java
read(sample, this::onRead);
```

The read method only needs to call the strategy, and then it will make use of the onRead method:

```java
public final <I, O> O read(final I sample, final Function<I, O> strategy) {
   return strategy.apply(sample);
}
```

### Constructor References

Constructors can be passed as arguments too.

```java
public final <I, O> O create(final I input, final Function<I, O> strategy);
```

```java
create(sample, Wrapper::new);
```

Not the constructor can be used as a Function:

```java
public final <I, O> O create(final I input, final Function<I, O> strategy) {
   return strategy.apply(sample);
}
```

Which is the same as:

```java
public final <I> Wrapper create(final I input) {
   return new Wrapper(sample);
}
```

### Static Method References

The same thing can be done with static methods:

```java
public final <I, O> O apply(final I input, final Function<I, O> strategy);
```

```java
apply(input, StringUtils::isNotBlank);
```

## Lambdas

Anonymous functions, or lambdas, can be used in a similar way:

```java
read(sample, (i) -> onRead(i));
```

This will create a Function which calls the onRead method with the received argument.

As functional interfaces have a single method the conversion won't be ambiguous. It can or can not transform the operation into the interface.

## Streams

Streams implement the pipeline pattern, chaining operations into a single flow.

Some common uses are filtering and mapping:

```java
final Collection<Wrapper> result;

result = strings.stream().filter(StringUtils::isNotBlank).map(Wrapper::new).collect(Collectors.toList());
```

### Stream From Iterable

Iterables don't give support to streams by default.

To create a stream from an iterable:

```java
StreamSupport.stream(iterable.spliterator(), false);
```

## Avoiding pass-through lambdas

The previous stream example could be like this:

```java
strings.stream().filter((s) -> StringUtils.isNotBlank(s)).map((s) -> new Wrapper(s)).collect(Collectors.toList());
```

But that uses lambdas just to pass arguments into functions or constructors. This can be reduced by using the other features which came with Java 8:

```java
strings.stream().filter(StringUtils::isNotBlank).map(Wrapper::new).collect(Collectors.toList());
```

## More Information

* [Java 8 Idioms](https://www.ibm.com/developerworks/java/library/j-java8idioms5/index.html)
* [Functional Interfaces in Java 8](http://www.baeldung.com/java-8-functional-interfaces)



