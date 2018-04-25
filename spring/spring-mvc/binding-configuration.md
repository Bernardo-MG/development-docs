# Binding Configuration

Controllers can define object binding:

```java
@ControllerAdvice
public final class GlobalBindingInitializer {

    /**
     * Sets the fields which can't be bound.
     * 
     * @param dataBinder
     *            data binder
     */
    @InitBinder
    public final void setDisallowedFields(final WebDataBinder dataBinder) {
        dataBinder.setDisallowedFields("id");
    }

}
```



