## Nested Type Errors

### Dependency Expecting a Child

Now we will use the repository when saving:

```java
public Iterable<ModelObject> save(final Iterable<ModelObject> data) {
   // ERROR: Iterable<ModelObject> is not Iterable<ModelObjectEntity>
   return repository.create(data);
}
```

### Method Receiving a Child

```java
Collection<ModelObjectEntity> data;

data = new ArrayList<>();

// ERROR: Iterable<ModelObjectEntity> is not Iterable<ModelObject>
service.save(data);
```

## Solving Nested Type Errors

### Removing Types

The easiest way, which is not recommended, is removing the nested type:

```java
public interface ModelObjectService {

   public Iterable save(final Iterable data);

}
```

```java
public Iterable save(final Iterable data) {
   // WARNING: type safety due to unchecked conversion
   return repository.create(data);
}
```

```java
Collection<ModelObjectEntity> data;

data = new ArrayList<>();

// There is not an error or warning
service.save(data);
```

### Transforming Types

Again, the types can be transformed:

```java
public Iterable<ModelObject> save(final Iterable<ModelObject> data) {
   final Iterable<ModelObjectEntity> entities;
   final Iterable<ModelObjectEntity> created;

   entities = StreamSupport.stream(data.spliterator(), false).map(this::toEntity).collect(Collectors.toList());

   created = repository.save(entities);

   return StreamSupport.stream(created.spliterator(), false).map(this::toObject).collect(Collectors.toList());
}
```

### Using Wildcard

```java
public interface ModelObjecService {

   public Iterable<? extends ModelObject> save(final Iterable<? extends ModelObject> data);

}
```

This works perfectly with the input:

```java
Collection<ModelObjectEntity> data;

data = new ArrayList<>();

// There is not an error or warning
service.save(data);
```

Requires the output to contain a wildcard:

```java
Collection<? extends ModelObject> output;

output = service.save(data);
```

And won't work with the inner dependency.

### Adding a Type

Again, the best solution is adding a type to the interface:

```java
public interface ModelObjecService<T extends ModelObject> {

   public Iterable<T> save(final Iterable<T> data);

}
```



