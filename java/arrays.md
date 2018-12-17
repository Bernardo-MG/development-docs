# Arrays

Collections of a single type. Try using collections before arrays.

## Creating Arrays

Defining the values:

```java
int[] integers = { 1, 2, 3 };
```

Defining size:

```java
int[] integers = int[3];
```

## Editing Arrays

```java
integers[0] = 10;
```

## Arrays as Variable Arguments

Variable arguments are handled as arrays

```java
public void someMethod(final Integer... values);
```

```java
someClass.someMethod(1, 2, 3);
```

## Utilities Class

The JDK offers the Arrays static class, with several helpful methods.



