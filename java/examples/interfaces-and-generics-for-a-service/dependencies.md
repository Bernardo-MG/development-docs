# Dependencies

Lets add a repository to handle those operations.

```java
public interface ModelObjectRepository {

   public ModelObjectEntity read(final ModelObjectEntity sample);

   public Iterable<ModelObjectEntity> create(final Iterable<ModelObjectEntity> sample);

}
```

As you see, the repository gives support only to ModelObjectEntity, not to ModelObjectAdditionalField.

