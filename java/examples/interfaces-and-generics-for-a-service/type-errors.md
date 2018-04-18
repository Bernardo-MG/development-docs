## Type Errors

### Dependency Expecting a Child

Lets try using the repository for reading:

```java
public ModelObject find(final ModelObject sample) {
   // ERROR: ModelObject is not ModelObjectEntity
   return repository.read(sample);
}
```

## Solving Type Errors

### Transforming the Input

One option is keeping the interface, and transforming the input:

```java
public ModelObject find(final ModelObject sample) {
   final ModelObjectEntity entitySample;

   entitySample = toEntity(sample);

   return repository.read(sample);
}

private ModelObjectEntity toEntity(final ModelObject sample) {
   final ModelObjectEntity entity;

   if(sample instanceof ModelObjectEntity) {
      entity = (ModelObjectEntity) sample;
   } else {
      entity = new ModelObjectEntity();
      // Copy properties
   }

   return entity;
}
```

### Adding a Type

Another is adding a type to the interface:

```java
public interface ModelObjecService<T extends ModelObject> {

   public T find(final T sample);

}
```



