# Other Operations

## Remove Duplicates

```java
final Collection<Object> filtered;

filtered = originalStream.distinct().collect(Collectors.toList());
```

## Sorting

```java
final Collection<Object> sorted;

sorted = originalStream.sorted().collect(Collectors.toList());
```

## Min and Max

```java
final Object value;

value = originalStream.min(comparator);
```

```java
final Object value;

value = originalStream.max(comparator);
```

## Numeric Ranges

```java
final Iterable<Short> years;

years = IntStream.range(startYear, endYear + 1).mapToObj(i -> (short) i).collect(Collectors.toList());
```

```java
final Iterable<Short> years;

years = IntStream.rangeClosed(startYear, endYear).mapToObj(i -> (short) i).collect(Collectors.toList());
```

## Limiting Size

```java
Stream<Integer> stream;

// Numbers 1 to 10
stream = Stream.iterate(1, n -> n).limit(10);
```

## Skipping Values

```java
Stream<Integer> stream;

// Numbers 5 to 10
stream = Stream.iterate(1, n -> n).skip(4).limit(10);
```

