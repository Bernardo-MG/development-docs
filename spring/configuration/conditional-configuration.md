# Conditional Configuration

## Configuration Class

Configuration classes can be loaded conditionally.

### Conditional by Property

```java
@Configuration
@ConditionalOnProperty(name = "property.name", matchIfMissing = false, havingValue = "true")
public class ConfigClass
```

### Conditional by Condition Class

```java
@Configuration
@Conditional(ConfigurationCondition .class)
public class ConfigClass
```

```java
public class ConfigurationCondition implements Condition
{

   public ConfigurationCondition()
   {
      super();
   }

   @Override
   public boolean matches(final ConditionContext context, final AnnotatedTypeMetadata metadata)
   {
      // Code
   }

}
```

### Conditional by Bean

Only if the bean exists:

```java
@Bean
public MainBean mainBean(){
   return new MainBean();
}

@Bean
@ConditionalOnBean(name="mainBean")
public Component component(){
   return new Component();
}
```

Only if the bean does not exist:

```java
@Bean
@ConditionalOnMissingBean(name="mainBean")
public Placeholder placeholder(){
   return new Placeholder();
}
```

### Conditional by Class

Only if the class is in the classpath:

```java
@Bean
@ConditionalOnClass(name="com.path.Driver")
public Driver driver(){
   return new Driver();
}
```

Only if the class is missing from the classpath:

```java
@Bean
@ConditionalOnMissingClass(name="com.path.Driver")
public AnotherDriver driver(){
   return new AnotherDriver ();
}
```

