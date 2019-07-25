# Mapping Controller Variables

Variables in the URL can be mapped into the controller arguments.

## Path Variables

These are part of the URL. For example in the following one the name at the end would be a variable:

```text
https://localhost:8080/users/John
```

Which can be mapped like this:

```java
@GetMapping(path="/{name}")
public final Employee getEmployee()
```

Regular expressions can be used:

```java
@GetMapping(path="/{name:[A-Za-z0-9]*}")
public final Employee getEmployee()
```

This can be applied to the controller mapping too:

```java
@RestController
@RequestMapping(value = "/users/{name}/")
public class EmployeeController
```

### Path Variables to Arguments

```java
@GetMapping(path="/{name}", produces = MediaType.APPLICATION_JSON_UTF8_VALUE)
public final Employee getEmployee(@PathVariable final String name)
```

### Path Variables to Objects

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

## Request Parameters

These come as a map added to the URL:

```text
https://localhost:8080/users?name=John
```

And can be mapped like this:

```java
@GetMapping
public final Employee getEmployee(@RequestParam(value = "name") final String name)
```

They can be optional:

```java
@GetMapping
public final Employee getEmployee(
   @RequestParam(value = "name", required = false, defaultValue = "") final String name)
```

