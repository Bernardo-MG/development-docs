# Collection

A generic interface for groups of objects. Used as a base interface for most traversable collections.

## Operations

* Add
* Remove
* Check existence

## Traversing

It can be iterated:

```java
col.iterator();
```

Or it can be operated with a stream:

```java
col.stream();
```

As it inherits from Iterable it can be used in for-each loops:

```java
for(String s : col)
```



