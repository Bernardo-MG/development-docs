# Other Operations

## Generating Numeric Ranges

```java
final Iterable<Short> years;

years = IntStream.range(startYear, endYear).mapToObj(i -> (short) i).collect(Collectors.toList());
```



