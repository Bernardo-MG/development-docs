## Type Errors

### Dependency Expecting a Child

We can't use the repository for finding data:

```java
public ModelObject find(final ModelObject sample) {
   // ERROR: ModelObject is not ModelObjectEntity
   return repository.read(sample);
}
```

## Solving Type Errors

### Transforming the Input

If we want to keep the interface then we need to transform the input object into a valid type.

There are two cases here:

* We have received an instance of the expected type, but the interface hides it
* We have received an instance of another type

In the first case we only need to cast the input. But in the other one we have to copy the properties into a new instance.

```java
public ModelObject find(final ModelObject sample) {
   final ModelObjectEntity entitySample;

   entitySample = toEntity(sample);

   return repository.read(sample);
}

private ModelObjectEntity toEntity(final ModelObject sample) {
   final ModelObjectEntity entity;

   if(sample instanceof ModelObjectEntity) {
      // The sample matches the expected type
      entity = (ModelObjectEntity) sample;
   } else {
      entity = new ModelObjectEntity();
      entity.setName(sample.getName());
   }

   return entity;
}
```

### Adding a Type

If we can change the interface another option is adding the type by using generics.

```java
public interface ModelObjectService<T extends ModelObject> {

   public T find(final T sample);

}
```

While this solves the problems, it also means that we will need a version of the service for each type.

```java
final ModelObjectService<ModelObjectEntity> = new ModelObjectService<>(repository);
final ModelObjectService<ModelObjectAdditionalField> = new ModelObjectService<>(dependency);
```

When using dependency injection we will need to take care of the type, making it harder to swap one version of the service for another.

