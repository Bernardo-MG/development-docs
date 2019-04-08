# Injecting Values

Any kind of object not supported by the bean injection system can be injected by using the @Value annotation and SpEL.

For example you can inject a property:

```java
@Value("${properties.valueName}")
```

More details can be found in the SpEL section.

## Types

The value usually is a primitive wrapper:

```java
public class ExampleService implements Service {

   @Value("${properties.valueName}")
   private Integer value;

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

