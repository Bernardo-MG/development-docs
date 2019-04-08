# Nested Type Errors

## Nested Type Errors

### Dependency Expecting a Child

If we try to use the repository for saving the data we end with a similar error:

```java
public Iterable<ModelObject> save(final Iterable<ModelObject> data) {
   // ERROR: Iterable<ModelObject> is not Iterable<ModelObjectEntity>
   return repository.create(data);
}
```

The difference here is that the type is inside the Iterable, used as a generic. Now we have to worry not only about the type we use, but also about the type inside the argument.

### Method Receiving a Child

Another version of the same problem is using as argument a collection of child classes. These will extend the interface we want, but won't match the expected generic template.

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

In short, this is already done by Java \(type erasure\), as generics are checked only when compiling. But we lose the most important feature of generics, ensuring that we are working with the data we want.

### Transforming Types

Again, we can keep the interfaces by transforming the type. But in this case we will have to transform all the objects we have received:

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

Another option is making use of the tools offered by generics:

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

But requires the output to use the wildcard:

```java
Collection<? extends ModelObject> output;

output = service.save(data);
```

And won't work with the inner dependency:

```java
public Iterable save(final Iterable<? extends ModelObject> data) {
   // ERROR: Iterable<? extends ModelObject> is not Iterable<ModelObjectEntity>
   return repository.create(data);
}
```

### Adding a Type

Again, the best solution is adding a type to the interface:

```java
public interface ModelObjecService<T extends ModelObject> {

   public Iterable<T> save(final Iterable<T> data);

}
```

And matching it with the type the dependencies want:

```java
final ModelObjecService<ModelObjectEntity> service = new ModelObjecServiceImpl<>(repository);
```

```java
public Iterable save(final Iterable<ModelObjectEntity> data) {
   // ERROR: Iterable<? extends ModelObject> is not Iterable<ModelObjectEntity>
   return repository.create(data);
}
```

