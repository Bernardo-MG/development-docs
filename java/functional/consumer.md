# Consumer

Takes an argument, but returns nothing. Used for operations with side effects.

```java
Consumer<String> consumer;

// Consumer initialization is skipped

consumer.accept("abc");
```

## Chaining Consumers

The default operations allow combining consumers:

```java
Consumer<String> consumer1;
Consumer<String> consumer2;
Consumer<String> firstThenSecond;

// Consumer initialization is skipped

// Apply consumer 1 then consumer 2
firstThenSecond = consumer1.andThen(consumer2);
```



