---
description: Interfaces and Generics for a Java Service
---

# Interfaces and Generics for a Service

Complex inheritance schemes can cause a lot of problems when two objects share a same root, but diverge too much from each other.

## Model

A model composed of:

* Interface
* JPA entity
* DTO with additional fields

```java
public interface ModelObject {

   public String getName();

   public void setName(final String name);

}

@Entity
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

## Service

```java
/**
* Service making use of the interface.
* <p>
* One method expects and returns the interface.
* <p>
* Another expects and returns an iterable of the interface.
*/
public interface ModelObjectService {

   /**
   * Returns an object matching the received sample.
   *
   * @param sample the sample
   * @returns an object matching the sample
   */
   public ModelObject find(final ModelObject sample);

   /**
   * Returns an object matching the received sample.
   *
   * @param data objects to save
   * @return all the objects which could be saved
   */
   public Iterable<ModelObject> save(final Iterable<ModelObject> data);

}
```

## Usage

```java
final ModelObjectAdditionalField sample;
final ModelObject found;

sample = new ModelObjectAdditionalField();

found = service.find(sample);
```

```java
final Collection<ModelObject> data;
final Iterable<ModelObject> created;

data.add(new ModelObjectEntity());
data.add(new ModelObjectAdditionalField());

created = service.save(data);
```



