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

When using Spring:

```java
@RunWith(JUnitPlatform.class)
@ExtendWith(SpringExtension.class)
@TestExecutionListeners({ DependencyInjectionTestExecutionListener.class })
@WebAppConfiguration
@ContextConfiguration(locations = { "classpath:context/config.xml" })
@TestPropertySource({ "classpath:config/config.properties" })
public class TestSuite {

}
```



