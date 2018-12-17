# Annotations

Beans can be annotated to indicate validations. They are set to fields. and these are some of the most common ones:

* AssertTrue
* Max
* Min
* NotNull

## Usage

```java
public class ValidatedClass {

   @NotNull
   private String field;

}
```

Applying validation groups:

```java
public class ValidatedClass {

   @NotNull(groups = { UpdateValidationGroup.class, CreateValidationGroup.class })
   private String field;

}
```

The groups can be any class or interface.

