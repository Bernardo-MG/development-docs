# Setting Up Tests

Tests need a runnable class, marked with @Test and a runner.

```java
@RunWith(JUnitPlatform.class)
public class TestSuite {

    @Test
    public final void sayHello() {
        Assert.assertEquals("Hello World!", new Greeter().sayHello());
    }

}
```



