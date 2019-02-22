# Mocking

## Create a Mock

```java
Service service;

service = Mockito.mock(Service.class);
```

## Set Return

```java
Mockito.when(service.operation(ArgumentMatchers.any()).thenReturn(values);
```
