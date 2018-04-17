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

Filtering:

```java
strings.stream().filter(StringUtils::isNotBlank);
```

Mapping:

```java
strings.stream().map(Wrapper::new);
```

Store in a list:

```java
strings.stream().collect(Collectors.toList());
```

## Stream From Iterable

Iterables don't give support to streams by default, but there is a utility class for this:

```java
StreamSupport.stream(iterable.spliterator(), false);
```

## Closing Streams

In some cases the streams can be working with an IO data source, or some other source which should be closed after being used. For that reason streams extend the AutoCloseable interface.

