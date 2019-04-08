# Disable Tests

To disable a test make use of the @Ignore/@Disabled annotation \(Junit 4/5\).

JUnit will report all the ignored tests. If they are commented, or the test annotations are removed, there is no way to know which tests have been disabled.

## Ignoring a Single Test

For Junit 4:

```java
@Ignore
@Test
public final void testCase() {
}
```

For Junit 5:

```java
@Disabled
@Test
public final void testCase() {
}
```

## Ignoring a Full Suite

```java
@Ignore
public final class TestSuite {

   @Test
   public final void testCase() {
   }

}
```

