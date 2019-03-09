# Setting Up Tests

Tests need a runnable class, marked with @Test and a runner.

```java
@RunWith(JUnitPlatform.class)
public class TestSuite {

    @Test
    public final void alwaysTrue() {
        Assert.assertTrue(true);
    }

}
```
