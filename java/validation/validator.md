# Validator

Java offers a validator interface.

## Usage

```java
Collection<ConstraintViolation<String>> constraintViolations;

constraintViolations = validator.validate(entidad);
```

Validating groups:

```java
constraintViolations = validator.validate(entidad, UpdateValidationGroup.class, CreateValidationGroup.class);
```



