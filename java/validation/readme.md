# Java Bean Validation

The JSR 380 specification takes care of bean validation, and offers an API for this:

```xml
<dependency>
   <groupId>javax.validation</groupId>
   <artifactId>validation-api</artifactId>
    <version>2.0.0.Final</version>
</dependency>
```

## Annotations

Beans can be annotated to indicate validations. They are set to fields. and these are some of the most common ones:

* AssertTrue
* Max
* Min
* NotNull

## Validator

Java offers a validator interface.



