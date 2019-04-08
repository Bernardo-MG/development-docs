# Mapping to Controller Methods

## Choosing Method by Param

Requests can be redirected to a method based on the params received:

```java
@GetMapping(produces = MediaType.APPLICATION_JSON_UTF8_VALUE)
public final Iterable<Employee> getEmployees(final Pageable page)

@GetMapping(produces = MediaType.APPLICATION_JSON_UTF8_VALUE, params = "admin=true")
public final Iterable<Employee> getEmployeesForAdmin(final Pageable page)

@GetMapping(produces = MediaType.APPLICATION_JSON_UTF8_VALUE, params = { "admin=true", "flag=true" } )
public final Iterable<Employee> getEmployeesForAdminAlternative(final Pageable page)
```

In this case the request will be redirected to getEmployeesForAdmin if the request includes the admin parameter with the value true. If the value is false, or the argument is missing, then getEmployees will be used.

## Choosing Method by Header

This works just like mapping through parameters:

```java
@GetMapping(produces = MediaType.APPLICATION_JSON_UTF8_VALUE, headers = "admin=true")
public final Iterable<Employee> getEmployeesForAdmin(final Pageable page)
```

## Choosing Method by Media Type

Another way of redirecting is by using the expected result type:

```java
@GetMapping(produces = MediaType.APPLICATION_JSON_UTF8_VALUE)
public final Iterable<Employee> getEmployeesJson(final Pageable page)

@GetMapping(produces = MediaType.TEXT_HTML_VALUE)
public final Iterable<Employee> getEmployeesHtml(final Pageable page)
```

This way the client can choose the data it receives, which can be useful for example for showing a default view in web services.

