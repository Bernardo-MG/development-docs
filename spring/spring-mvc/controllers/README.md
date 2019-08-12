# Controllers

Controllers are easy to implement:

```java
@Controller
@RequestMapping("/")
public class HomeController
```

HTTP operations are mapped with specific annotations:

```java
@GetMapping(produces = MediaType.TEXT_HTML_VALUE)
public final String showWelcome()
```

All the HTTP verbs can be mapped. This can be chosen by usin the specific annotations or the generic one:

```java
@RequestMapping(method = RequestMethod.GET, produces = MediaType.TEXT_HTML_VALUE)
public final String showWelcome()
```

## REST Controller

There is a specific annotation for REST controllers:

```java
@RestController
@RequestMapping("/employees")
public class EmployeeController
```

This adds the @ResponseBody annotation, indicating that the values returned by annotated methods will be stored in the response body.

Otherwise operations make use of the same mappings:

```java
@GetMapping(produces = MediaType.APPLICATION_JSON_UTF8_VALUE)
public final Iterable<Employee> getEmployees(final Pageable page)
```

