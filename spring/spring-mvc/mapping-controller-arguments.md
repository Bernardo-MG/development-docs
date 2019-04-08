# Mapping Controller Variables

Variables in the URL can be mapped into the controller arguments.

For example, having this URL:

```text
https://localhost:8080/controller/John
```

## Path Variables

```java
@GetMapping(path="/{name}", produces = MediaType.APPLICATION_JSON_UTF8_VALUE)
public final Employee getEmployee()
```

Regular expressions can be used:

```java
@GetMapping(path="/{name:[A-Za-z0-9]*}", produces = MediaType.APPLICATION_JSON_UTF8_VALUE)
public final Employee getEmployee()
```

This can be applied to the controller mapping too:

```java
@RestController
@RequestMapping(value = "/controller/{organization}/")
public class EmployeeController
```

## Path Variables to Arguments

```java
@GetMapping(path="/{name}", produces = MediaType.APPLICATION_JSON_UTF8_VALUE)
public final Employee getEmployee(@PathVariable final String name)
```

## Path Variables to Objects

```java
@GetMapping(path="/{name}", produces = MediaType.APPLICATION_JSON_UTF8_VALUE)
public final Employee getEmployee(final EmployeeName name)
```

This requires EmployeeName being a bean with a field sharing the path variable name:

```java
public final class EmployeeName {

   private String name;

   public EmployeeName () {
      super();
   }

   public final String getName() {
      return name;
   }

   public final void setName(final String n) {
      name = n;
   }

}
```

