---
description: Java Streams
---

# Streams

Streams implement the pipeline pattern, chaining operations into a single flow.

Some common uses are filtering and mapping:

```java
final Collection<Wrapper> result;

result = strings.stream().filter(StringUtils::isNotBlank).map(Wrapper::new).collect(Collectors.toList());
```

## Generation

### Stream From Array

```java
Stream<String> stream;

stream  = Stream.of("abc", "def");
```

### Stream From Iterable

Iterables don't give support to streams by default, but there is a utility class for this:

```java
Iterable<String> strings;
Stream<String> stream;

stream = StreamSupport.stream(strings.spliterator(), false);
```

### Empty Stream

```java
Stream<String> empty;

empty = Stream.empty();
```

### From Supplier

```java
Stream<String> stream;
Supplier<String> supplier;

supplier = this::operation;

stream = Stream.generate(supplier);
```

### Builder

```java
Stream<String> stream;
Supplier<String> supplier;

supplier = this::operation;

stream = Stream.builder().add("text").build();
```

### Iteration

```java
Stream<Integer> stream;

// Numbers 1 to 10
stream = Stream.iterate(1, n -> n).limit(10);
```

### From Other Streams

```java
Stream<String> stream;

stream = Stream.concat(streamA, streamB);
```

## Closing Streams

In some cases the streams can be working with an IO data source, or some other source which should be closed after being used. For that reason streams extend the AutoCloseable interface.

