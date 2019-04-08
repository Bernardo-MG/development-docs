# Dependencies

Lets add a repository to handle those operations.

This will cause problems, as it works only with ModelObjectEntity.

```java
public interface ModelObjectRepository {

   public ModelObjectEntity read(final ModelObjectEntity sample);

   public Iterable<ModelObjectEntity> create(final Iterable<ModelObjectEntity> sample);

}
```

