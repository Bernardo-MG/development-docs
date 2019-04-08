# Model Attributes

To load the initial values for a model attribute:

```java
@ModelAttribute(ExampleEntityViewConstants.BEAN_FORM)
public final ExampleEntityForm getEntityForm() {
    return new ExampleEntityForm();
}
```

This same annotation can be used to acquire the value:

```java
@PostMapping
public final String saveEntity(final ModelMap model,
        @ModelAttribute(ExampleEntityViewConstants.BEAN_FORM) @Valid final ExampleEntityForm form,
        final BindingResult bindingResult, final HttpSession session)
```

