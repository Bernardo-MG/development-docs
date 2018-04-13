---
description: Transactions Tests with Spring
---

# Transactional Tests

To create a transactional integration test with JUnit 4:

```java
@ContextConfiguration(locations = { "classpath:context/test-db-context.xml" })
public class ITRepository extends AbstractTransactionalJUnit4SpringContextTests
```



