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

Remove all the null values:

```java
Collection<Object> collection;

// Collection is initialized

collection.stream().filter(Objects::nonNull);
```

### Map

Transform one object into another.

```java
strings.stream().map(Wrapper::new);
```

### Flat Map

Transform into an stream and merge.

```java
strings.stream().flatMap(this:splitString);
```

```java
public Stream<String> splitString(final String str);
```

```java
Collection<Stream<String>> mapped;
Collection<String> flattened;

mapped = strings.stream().map(this:splitString).collect(Collectors.toList());

flattened = strings.stream().flatMap(this:splitString).collect(Collectors.toList());
```

### Reduce

```java
integers.stream().reduce(this::sum);
```

```java
integers.stream().sum();
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

Store in a map:

```java
Map<String, Named> map = objs.stream().collect(Collectors.toMap(Named::getName, Function.identity()));
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

