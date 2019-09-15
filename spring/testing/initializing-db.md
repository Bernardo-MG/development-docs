# Initializing DB

The SQL annotation will load the specified scripts.

```java
@Sql({ "/testconf/db/initialData.sql" })
public class Test
```

```java
@Sql({ "/testconf/db/additionalData.sql" })
public void testMethod()
```

