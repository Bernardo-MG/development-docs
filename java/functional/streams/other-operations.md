# Other Operations

## Generating Numeric Ranges

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

```
Stream<Integer> stream;

// Numbers 5 to 10
stream = Stream.iterate(1, n -> n).skip(4).limit(10);
```



