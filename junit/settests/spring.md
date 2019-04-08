# Dependencies with Spring

Spring will need a bit of additional configuration to allow injecting dependencies.

```java
@RunWith(JUnitPlatform.class)
@ExtendWith(SpringExtension.class)
@TestExecutionListeners({ DependencyInjectionTestExecutionListener.class })
@WebAppConfiguration
@ContextConfiguration(locations = { "classpath:context/config.xml" })
@TestPropertySource({ "classpath:config/config.properties" })
public class TestSuite {

    @Autowired
    private Service testedService;

    @Test
    public final void alwaysTrue() {
        final Boolean success;

        success = testedService.call();

        Assert.assertTrue(success);
    }

}
```

