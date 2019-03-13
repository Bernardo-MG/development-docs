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

## Closing Streams

In some cases the streams can be working with an IO data source, or some other source which should be closed after being used. For that reason streams extend the AutoCloseable interface.

