---
description: Functional Programming in Java
---

# Functional Programming

Java 8 gave support to functional programming in Java.

Several patterns are supported, such as consumers, streams or functions, allong operations such as mapping and filtering.

## Functional Interface

Functional interfaces, marked with the @FunctionalInterface annotation, are single method interfaces. These are very useful when working with the functional paradigm, as it is easy to ensure they will have a single concern.

```java
@FunctionalInterface
public interface Function<T, R>
```

### Function

The Function interface allows chaining functions by using the compose and andThen methods.

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

```
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

```
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

## Lambdas

Anonymous functions, or lambdas, can be used in a similar way:

```java
read(sample, (i) -> onRead(i));
```

This will create a Function which calls the onRead method with the received argument.

As functional interfaces have a single method the conversion won't be ambiguous. It can or can not transform the operation into the interface.

## Streams

Streams allow working with data collection as a continuous flow, which can be chained to other flows.

For example it is possible filtering data and then mapping it to another object:

```java
final Collection<Wrapper> result;

result = strings.stream().filter((s) -> StringUtils.isNotBlank(s)).map((s) -> new Wrapper(s)).collect(Collectors.toList());
```

### Stream From Iterable

Iterables don't give support to streams by default.

To create a stream from an iterable:

```java
StreamSupport.stream(iterable.spliterator(), false);
```

## Avoiding pass-through lambdas

The stream example uses lambdas just to pass an argument to a function or constructor.

```java
filter((s) -> StringUtils.isNotBlank(s))
```

```java
map((s) -> new Wrapper(s))
```

By using the other functional patterns, these can be reduced like this:

```
filter(StringUtils::isNotBlank)
```

```
map(Wrapper::new)
```



