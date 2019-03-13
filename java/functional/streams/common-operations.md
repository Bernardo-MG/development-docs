# Common Operations

## Collect

Store in a list:

```java
List<String> list;

list = strings.stream().collect(Collectors.toList());
```

Store in a string:

```java
String string;

string = strings.stream().collect(Collectors.joining(", "));
```

Store in a map:

```java
Map<String, Named> map;

map  = objs.stream().collect(Collectors.toMap(Named::getName, Function.identity()));
```

## Filter

Remove values.

```java
Collection<Object> collection;
Collection<Object> filtered;

// Collection is initialized

// Removes null values
filtered = collection.stream().filter(Objects::nonNull).collect(Collectors.toList());
```

## Map

Transform one object into another.

```java
Collection<String> strings;
Collection<Wrapper> wrapped;

// Collection is initialized

// Wraps values
wrapped = strings.stream().map(Wrapper::new).collect(Collectors.toList());
```

## Flat Map

Transform into an stream and merge.

```java
public interface AdressBook {

   public Collection<String> getAdresses();

}
```

```java
Collection<AdressBook> books;
Collection<String> addresses;

// Collection is initialized

// Collects all the addresses from all the address books
addresses = books.stream().flatMap((b) -> b.getAdresses().stream()).collect(Collectors.toList());
```

## Reduce

Combines all the values.

```java
Collection<Integer> integers;
Integer sumation;

// Collection is initialized

// All the values are added together
sumation = integers.stream().reduce(this::sum);
```

Some streams include the most common reduction functions:

```java
integers.stream().sum();
```

## Consume

Apply a function to all the elements.

```java
Collection<Integer> integers;

// Collection is initialized

// Increases all the values
integers.stream().forEach(this::increase);
```

## Concatenate

Combine streams.

```java
Collection<Integer> list1;
Collection<Integer> list2;
Collection<Integer> allValues;

// Collections are initialized

// Combines collections
allValues = Stream.concat(list1.stream(), list2.stream).collect(Collectors.toList());
```



