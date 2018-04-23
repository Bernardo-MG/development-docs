# Error Handling

Aspects can be used to take care of controller exceptions:

```java
@ControllerAdvice
public final class ControllerExceptionHandler {

   // More code

   @ExceptionHandler(IllegalArgumentException.class)
   @ResponseStatus(HttpStatus.BAD_REQUEST)
   @ResponseBody
   public final ErrorResponse processIllegalArgument(final IllegalArgumentException ex) {
      LOGGER.debug("Intercepted IllegalArgumentException");

      return new DefaultErrorResponse(resolveLocalizedErrorMessage(ex.getMessage()));
   }

   // More Code

}
```

## Default Implementation

There is an abstract class to ease creating exception handlers:

```java
@ControllerAdvice
public class DefaultErrorHandler extends ResponseEntityExceptionHandler
```

## Overriding

Exception handling can be overriden for expecific controllers:

```java
@ControllerAdvice(assignableTypes = { EmployeeController.class })
@Order(Ordered.HIGHEST_PRECEDENCE)
public class EmployeeErrorHandler
```



