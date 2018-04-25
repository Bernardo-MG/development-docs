# Controller Advices

By using aspects controllers can receive common configurations. This requires just annotating a class like this:

```java
@ControllerAdvice
public final class GlobalControllerConfig
```

It may also define specific controllers:

```java
@ControllerAdvice(assignableTypes = { EmployeeController.class })
@Order(Ordered.HIGHEST_PRECEDENCE)
public class EmployeeControllerConfig
```

This can contain global configuration through annotations such as @ExceptionHandler, @InitBinder or @ModelAttribute.

## Testing

Always remember to add the required advices to MVC tests:

```java
getMockMvcBuilder().setControllerAdvice(new EmployeeControllerConfig())
```



