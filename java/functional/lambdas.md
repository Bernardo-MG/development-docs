---
description: Java Lambdas
---

# Lambdas

Anonymous functions, or lambdas, can be used to instantiate functional interfaces.

Having these methods:

```java
public final <I, O> O read(final I sample, final Function<I, O> strategy);

protected <I, O> O onRead(final I sample){
   // This would encapsulate the code
}
```

They can be used like this:

```java
read(sample, (i) -> onRead(i));
```

This will create a Function which calls the onRead method with the received argument.

As functional interfaces have a single method the conversion won't be ambiguous. It can or can not transform the operation into the interface.

## Avoiding pass-through lambdas

The previous example is using a lambda just to pass an argument to the function. This can be avoided by using the other functional patterns:

```text
read(sample, this::onRead);
```

Avoid using lambdas just to pass arguments into functions.

