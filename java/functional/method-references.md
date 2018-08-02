---
description: Method References
---

# Method References

Methods can be passed as arguments for functions. These are not actual method references, but more an auto mapping feature, which wraps methods into an interface implementation.

Lets suppose we have these methods:

```java
public final <I, O> O read(final I sample, final Function<I, O> strategy);

protected <I, O> O onRead(final I sample){
   // This would encapsulate the code
}
```

It is possible using onRead as the strategy argument:

```java
read(sample, this::onRead);
```

The read method only needs to call the strategy, and then it will make use of the onRead method, making these two operations equivalent:

```java
public final <I, O> O read(final I sample, final Function<I, O> strategy) {
   return strategy.apply(sample);
}

public final <I, O> O read(final I sample) {
   return onRead(sample);
}
```

## Constructor References

Constructors can be passed as arguments too.

```java
public final <I, O> O create(final I input, final Supplier<I, O> strategy);
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

## Static Method References

The same thing can be done with static methods:

```java
public final <I, O> O apply(final I input, final Function<I, O> strategy);
```

```java
apply(input, StringUtils::isNotBlank);
```



