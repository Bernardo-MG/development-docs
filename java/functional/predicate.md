# Predicate

A logical predicate, which can be combined with or and and operations, or negated.

```java
Predicate<Integer> predicate;
Boolean result;

// Predicate initialization is skipped

result = predicate.test(12);
```

## Logical Operations

The interface contains default methods for boolean operations:

```java
Predicate<Integer> predicate1;
Predicate<Integer> predicate2;
Predicate<Integer> alwaysTrue;
Predicate<Integer> alwaysFalse;
Predicate<Integer> both;
Predicate<Integer> one;

// Predicate initialization is skipped

// True if both are true
both = predicate1.and(predicate2);

// True if one is true
one = predicate1.or(predicate2);

// Reversed
alwaysFalse = alwaysTrue.negate();
```

## Extensions

Just like with functions there is a BiPredicate and a few extensions for numeric primitives.

