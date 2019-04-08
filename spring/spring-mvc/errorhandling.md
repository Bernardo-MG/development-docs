# Error Handling

A controller advice can be used to take care of exception handling:

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

The @ExceptionHandler defines the exception to capture, and @ResponseStatus the status for the response.

## Default Implementation

There is an abstract class to ease creating exception handlers:

```java
@ControllerAdvice
public class DefaultErrorHandler extends ResponseEntityExceptionHandler
```

