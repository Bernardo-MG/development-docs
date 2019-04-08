# Using Classes

If you know the specific class you want, it can be used to generate a new instance:

```java
public class ModelObjectBuilderWithClass<V extends ModelObject> implements ModelObjectBuilder<V> {

   private final Class<V> clz;

   public ModelObjectBuilderWithClass(final Class<V> clazz) {
      super();

      clz = clazz;
   }

   public V getModelObject(final String name) {
      final V obj;

      try {
         obj = clazz.newInstance();
      } catch (final InstantiationException | IllegalAccessException e) {
         throw new RuntimeException(e);
      }

      obj.setName(name);

      return obj;
   }

}
```

```java
new ModelObjectBuilderWithClass(ModelObjectImpl.class);
```

## Downsides

* Handling exceptions

