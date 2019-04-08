# Creating New Instances Dynamically

Sometimes the type of an object is decided at runtime.

In this example the model consists of a single interface, and no implementation. The user is expected to choose the actual implementation to use.

## Model

```java
public interface ModelObject {

   public String getName();

   public void setName(final String name);

}
```

## Component

```java
public interface ModelObjectBuilder<V extends ModelObject> {

   public V getModelObject(final String name);

}
```

