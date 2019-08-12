# Request Argument Validation

Spring will apply Java Bean Validations to controller arguments if they are annotated:

```java
@GetMapping(produces = MediaType.TEXT_HTML_VALUE)
public final String readData(@Valid final EmployeeData employee)
```

If the received bean is prepared for Java Bean Validation these validations will be applied and a exception thrown if any fails.

