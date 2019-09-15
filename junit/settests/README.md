# Setting Up Tests

## JUnit 4

```java
public class TestSuite {

    @Test
    public final void alwaysTrue() {
        Assert.assertTrue(true);
    }

}
```

## JUnit 5

The newer version need a runnable class, marked with @Test and a runner.

Some annotations may be named the same, but they come from other packages.

Most importantly, the assertions now come from a different class.

```java
@RunWith(JUnitPlatform.class)
public class TestSuite {

    @Test
    public final void alwaysTrue() {
        Assertions.assertTrue(true);
    }

}
```

