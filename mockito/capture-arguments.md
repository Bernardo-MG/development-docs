# Capture Arguments

```java
final ArgumentCaptor<Short> captor;
final Short captured;

captor = ArgumentCaptor.forClass(Short.class);

Mockito.verify(service).operation(captor.capture());

captured = captor.getValue();
		pageable = captor.getValue();
Mockito.when(service.operation(captor.capture()).thenReturn(values);
```



