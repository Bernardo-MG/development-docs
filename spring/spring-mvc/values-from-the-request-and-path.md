# Values from the Request and Path

Lets suppose we have this controller:

```java
@Controller
@RequestMapping("/path")
public class EmployeeController
```

## Request Parameters

To get a parameter from the request:

```java
@GetMapping
public final Iterable<Employee> readEmployees(
   @RequestParam(value = "company", required = false, defaultValue = "") final String company)
```

When using the [http://www.somewhere.com/path?company=abc](http://www.somewhere.com/path?company=abc) URL then the company value will be abc.

## Path Variables

To get a variable from the path:

```java
@GetMapping(path = "/{company:[0-9a-zA-Z]*}")
public final Iterable<Employee> readEmployees(@PathVariable("company") final String company)
```

When using the [http://www.somewhere.com/path/abc](http://www.somewhere.com/path/abc) URL then the company value will be abc.

