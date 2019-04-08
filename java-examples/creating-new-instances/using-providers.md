# Using Providers

Java 8 added the provider interface, which eases creating new instances:

```java
public class ModelObjectBuilderWithProvider<V extends ModelObject> implements ModelObjectBuilder<V> {

   private final Provider<V> provider;

   public ModelObjectBuilderWithProvider(final Provider<V> prov) {
      super();

      provider = prov;
   }

   public V getModelObject(final String name) {
      final V obj;

      obj = provider.get();
      obj.setName(name);

      return obj;
   }

}
```

```java
new ModelObjectBuilderWithProvider(ModelObjectImpl::new);
```

