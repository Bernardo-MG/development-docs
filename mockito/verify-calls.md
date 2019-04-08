# Verify Calls

Check it was called once, and only once:

```java
Mockito.verify(service, Mockito.times(1)).method(ArgumentMatchers.any());
```

Check it was called one or more times:

```java
Mockito.verify(service, Mockito.atLeastOnce()).method(ArgumentMatchers.any());
```

