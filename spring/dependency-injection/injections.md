# Injections

## Field

```java
public class ExampleService implements Service {

   @Autowired
   private Component dependency;

   public ExampleService() {
      super();
   }

}
```

## Constructor

```java
public class ExampleService implements Service {

   private final Component dependency;

   @Autowired   
   public ExampleService(final Component component) {
      super();

      dependency = component;
   }

}
```

## Setter

```java
public class ExampleService implements Service {

   private Component dependency;

   public ExampleService() {
      super();
   }

   @Autowired
   public void setDependency(final Component component) {
      dependency = component;
   }

}
```

## Specifying

```java
public class ExampleService implements Service {

   @Autowired
   @Qualifier("dependencyB")
   private Component dependency;

   public ExampleService() {
      super();
   }

}
```

