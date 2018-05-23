# Injecting Values

Any kind of object not supported by the bean injection system can be injected by using the @Value annotaion and SpEL.

These can be injected from properties:

```java
@Value("${properties.valueName}")
```

Or by name if they were added to the context:

```java
@Value("#{@valuesCollection}")
```

It also supports default values:

```java
@Value("${properties.booleanValue:false}")
```

The value usually is a primitive wrapper:

```java
public class ExampleService implements Service {

   @Value("${properties.valueName}")
   private String value;

   public ExampleService() {
      super();
   }

}
```

Or a collection:

```java
public class ExampleService implements Service {

   @Value("#{@valuesCollection}")
   private Iterable<Integer> values;

   public ExampleService() {
      super();
   }

}
```



