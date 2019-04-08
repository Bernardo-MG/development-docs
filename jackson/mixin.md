# Mixin

A mixin sets the Jackson configuration into an interface.

```java
public interface Employee {

   public String getName();

   public void setName(final String name);

}
```

```java
@JsonAutoDetect(getterVisibility = JsonAutoDetect.Visibility.NONE,
        isGetterVisibility = JsonAutoDetect.Visibility.NONE)
public interface EmployeeMixIn extends Employee {

   @Override
   @JsonProperty
   public String getName();

}
```

This can then be added to a context:

```java
public void setupMixIns(final SetupContext context) {
   context.setMixInAnnotations(Employee.class, EmployeeMixIn.class);
}
```

