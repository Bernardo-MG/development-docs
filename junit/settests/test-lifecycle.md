# Test Lifecycle

## JUnit 5

Special annotations will call method at specific points on the test lifecycle.

* AfterAll
* AfterEach
* BeforeAll
* BeforeEach

This can be used for example to initialize data for the test:

```java
@RunWith(JUnitPlatform.class)
public class TestSuite {

    @BeforeAll
    public final void setUpData() {
        // Loads tests data
    }

}
```



