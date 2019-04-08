# Other Operations

## Remove Repeated

```java
Collection<Object> collection;
Collection<Object> filtered;

// Collection is initialized

// Removes repeated values
filtered = collection.stream().distinct().collect(Collectors.toList());
```

## Sorting

```java
Collection<Object> collection;
Collection<Object> filtered;

// Collection is initialized

// Sorts values
filtered = collection.stream().sorted().collect(Collectors.toList());
```

## Min and Max

```java
Collection<Object> collection;
Object value;

// Collection is initialized

// Removes repeated values
value = collection.stream().min(comparator);
```

```java
Collection<Object> collection;
Object value;

// Collection is initialized

// Removes repeated values
value = collection.stream().max(comparator);
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

