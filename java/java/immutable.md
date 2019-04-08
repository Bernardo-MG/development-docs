# Immutable and Unmodifiable

## Immutable and Unmodifiable

## Immutable

JDK utilities classes can be used to generate immutable empty collections:

```java
Collections.emptyList();
Collections.emptyMap();
```

Immutable empty collections will reject values.

## Unmodifiable

These same classes can be used to wrap standard containers and make them unmodifiable:

```java
Iterables.unmodifiableIterable(samples);
Collections.unmodifiableMap(params);
```

While it isn't possible modifying this wrapper the original collection may still change.

