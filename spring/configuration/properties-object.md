# Properties Object

Spring Boot supports mapping properties into an object, to have better control over existing configuration.

### Automatic Mapping

In this case it will map all the values starting with "db." into any matching field.

```java
@Validated
@ConfigurationProperties(prefix = "db")
public class DatabaseProperties
{

   @NotEmpty
   private String url;

   public final String getUrl()
   {
      return url;
   }

}
```

### Value Injection

In some cases it won't me possible, mostly when the properties structure isn't clean, and then the values will have to be injected.

```java
@Validated
@ConfigurationProperties
public class DatabaseProperties
{

   @NotEmpty
   @Value("${db.url}")
   private String url;

   @NotEmpty
   @Value("${username.db}")
   private String username;

   public final String getUrl()
   {
      return url;
   }

   public final String getUsername()
   {
      return username;
   }

}
```

### Registering and Using

These files can be registered into any configuration class.

```java
@Configuration
@EnableConfigurationProperties(DatabaseProperties.class)
public class ConfigurationClass
```

And then the properties class can be injected as a dependency.

```java
@Bean
public DataSource datasource(DatabaseProperties dbProperties)
```

