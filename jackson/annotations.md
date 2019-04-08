# Annotations

## JsonIgnoreProperties

Allows ignoring properties, avoiding possible problems when deserializing.

```java
@JsonIgnoreProperties(ignoreUnknown = true)
public class Employee
```

## JsonTypeInfo

Used to handle inheritance and polymorphic classes.

```java
@JsonTypeInfo(use = JsonTypeInfo.Id.CLASS, include = JsonTypeInfo.As.PROPERTY, property = "className")
public class Employee

public class ExtendedEmployee extends Employee
```

Now the ExtendedEmployee can be serialized and deserialized using Employee as a reference. Jackson will know the actual type of Employee to use.

### JsonSubTypes

Used along JsonTypeInfo to indicate the inheritance hierarchy.

```java
@JsonTypeInfo(use = JsonTypeInfo.Id.NAME, include = JsonTypeInfo.As.PROPERTY, property = "type")
@JsonSubTypes({
   @Type(value = EmployeeExtended.class, name = "extended"),
   @Type(value = EmployeeAdvanced.class, name = "advanced")
})
public class Employee
```

