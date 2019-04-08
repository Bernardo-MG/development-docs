# Testing Exceptions

## JUnit 4

There are two options to test an exception with JUnit 4.

### Annotation

```java
@Test(expected = Exception.class)
public final void testWithException() {
   service.throwsException();
}
```

### Rule

```java
@Rule
public ExpectedException expectedEx = ExpectedException.none();

@Test
public final void testWithException() {
   expectedEx.expect(Exception.class);
   expectedEx.expectMessage("error.message");

   service.throwsException();
}
```

## JUnit 5

```java
@Test
public final void testWithException() {
   Assertions.assertThrows(
      Exception.class,
      service::throwsException);
}
```

