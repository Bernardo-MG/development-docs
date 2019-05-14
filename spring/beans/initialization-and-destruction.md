# Initialization and Destruction

## Initialization

With annotations:

```java
public class Bean {

   @PostConstruct
   public void initialize() {
      // Code
   }

}
```

With the interface:

```java
public class Bean implements InitializingBean {

   @Override
   public void afterPropertiesSet() throws Exception {
      // Code
   }

}
```

## Destruction

With annotations:

```java
public class Bean {

   @PreDestroy
   public void destroy() {
      // Code
   }

}
```

With the interface:

```java
public class Bean implements DisposableBean {

   @Override
   public void destroy() throws Exception {
      // Code
   }

}
```

