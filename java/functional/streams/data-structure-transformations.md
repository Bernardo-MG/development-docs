# Data Structure Transformations

## To String

```java
final String employees;

employees = empStream.map(Employee::getName).collect(Collectors.joining(", "));
```

## To Map

```java
final Map<Long, Employee> employees;

employees = empStream.collect(Collectors.toMap(Employee::getId, Function.identity()));
```

## To Map of Lists

```java
final Map<String, List<Employee>> employees;

employees = empStream.collect(Collectors.groupingBy(Employee::getCity));
```

