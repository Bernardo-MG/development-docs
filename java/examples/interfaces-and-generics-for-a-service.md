---
description: Interfaces and Generics for a Java Service
---

# Interfaces and Generics for a Service

Complex inheritance schemes can cause a lot of problems when two objects share a same root, but diverge too much from each other.

```java
public interface ModelObject {

   public String getName();

   public void setName();

}

public class ModelObjectEntity implements ModelObject {

   // Class prepared for persistence

   public Integer getId() {
      return id;
   }

}

public class ModelObjectAdditionalField implements ModelObject {

   // Implements the interface, but adds a field

   public Integer getDate() {
      return date;
   }

}
```

Now, you have a service which works with the interface:

```java
public interface ModelObjecService {

   /**
   * Returns an object matching the received sample.
   *
   * @param sample the sample
   * @returns an object matching the sample
   */
   public ModelObject find(final ModelObject sample);

}
```

This works perfectly:

```java
ModelObject found;
ModelObjectAdditionalField sample;

sample = new ModelObjectAdditionalField();

found = service.find(sample);
```

Except when it doesn't.

## Type Errors

### Dependency Expecting a Child

Now, let's suppose there is a version of the service using a repository for finding the object:

```java
public interface ModelObjecRepository {

   public ModelObjectEntity read(final ModelObjectEntity sample);

}
```

This won't even compile:

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

## Nested Type

Lets add another method to the service:

```java
public interface ModelObjecService {

   /**
   * Returns an object matching the received sample.
   *
   * @param data objects to save
   * @return all the objects which could be saved
   */
   public Iterable<ModelObject> save(final Iterable<ModelObject> data);

}
```

Which works like this:

```java
List<ModelObject> data;

data.add(new ModelObjectEntity());
data.add(new ModelObjectAdditionalField());

service.save(data);
```

## Nested Type Errors

### Dependency Expecting a Child

We will use the repository example again:

```java
public interface ModelObjecRepository {

   public Iterable<ModelObjectEntity> create(final Iterable<ModelObjectEntity> sample);

}
```

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
public interface ModelObjecService {

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



