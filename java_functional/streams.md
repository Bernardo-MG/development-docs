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

## Common Operations

### Filter

```java
strings.stream().filter(StringUtils::isNotBlank);
```

### Map

```java
strings.stream().map(Wrapper::new);
```

### Consume

```java
integers.stream().forEach(this::increase);
```

### Collect

Store in a list:

```java
List<String> list = strings.stream().collect(Collectors.toList());
```

Store in a string:

```java
String string = strings.stream().collect(Collectors.joining(", "));
```

### Concatenate

Streams can be combined:

```java
Stream.concat(list1.stream(), list2.stream);
```

### Generate

```
Stream<String> stream = Stream.of(string1, string2);
```

## Stream From Iterable

Iterables don't give support to streams by default, but there is a utility class for this:

```java
StreamSupport.stream(iterable.spliterator(), false);
```

## Closing Streams

In some cases the streams can be working with an IO data source, or some other source which should be closed after being used. For that reason streams extend the AutoCloseable interface.
