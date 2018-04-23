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

## Choosing Method by Param

Requests can be redirected to a method based on the params received:

```java
@GetMapping(produces = MediaType.APPLICATION_JSON_UTF8_VALUE)
public final Iterable<Employee> getEmployees(final Pageable page)

@GetMapping(produces = MediaType.APPLICATION_JSON_UTF8_VALUE, params = "admin=true")
public final Iterable<Employee> getEmployeesForAdmin(final Pageable page)
```

In this case the request will be redirected to getEmployeesForAdmin if the request includes the admin parameter with the value true. If the value is false, or the argument is missing, then getEmployees will be used.

## Choosing Method by Media Type

Another way of redirecting is by using the expected result type:

```java
@GetMapping(produces = MediaType.APPLICATION_JSON_UTF8_VALUE)
public final Iterable<Employee> getEmployeesJson(final Pageable page)

@GetMapping(produces = MediaType.TEXT_HTML_VALUE)
public final Iterable<Employee> getEmployeesHtml(final Pageable page)
```

This way the client can choose the data it receives, which can be useful for example for showing a default view in web services.

