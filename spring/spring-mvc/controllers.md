# Controllers

Controllers are easy to implement:

```
@Controller
@RequestMapping("/")
public class HomeController
```

HTTP operations are mapped with specific annotations:

```
@GetMapping(produces = MediaType.TEXT_HTML_VALUE)
public final String showWelcome()
```

## REST Controller

There is a specific annotation for REST controllers:

```
@RestController
@RequestMapping("/employees")
public class EmployeeController
```

This adds the @ResponseBody annotation, indicating that the values returned by annotated methods will be stored in the response body.

Otherwise operations make use of the same mappings:

```
@GetMapping(produces = MediaType.APPLICATION_JSON_UTF8_VALUE)
public final Iterable<Employee> getEmployees(final Pageable page)
```
