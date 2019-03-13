# Searching for Values

## Find

```java
Collection<Object> collection;
Object found;

// Collection is initialized

// Returns the first value which is not null
found = collection.stream().filter(Objects::nonNull).findFirst();

// Returns a value, which may not be the first, which is not null
found = collection.stream().filter(Objects::nonNull).findAny();
```

## Match

```java
Boolean exists;

// Checks that at least one value is not null
exists = collection.stream().anyMatch(Objects::nonNull);
```

```
Boolean exists;

// Checks that all the values are null
exists = collection.stream().allMatch(Objects::nonNull);
```

```
Boolean exists;

// Checks that no value is null
exists = collection.stream().noneMatch(Objects::nonNull);
```



