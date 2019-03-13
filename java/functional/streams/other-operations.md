# Other Operations

## Empty Stream

```java
Stream<String> empty;

empty = Stream.empty();
```

## Generating Numeric Ranges

```java
final Iterable<Short> years;

years = IntStream.range(startYear, endYear + 1).mapToObj(i -> (short) i).collect(Collectors.toList());
```

```java
final Iterable<Short> years;

years = IntStream.rangeClosed(startYear, endYear).mapToObj(i -> (short) i).collect(Collectors.toList());
```



