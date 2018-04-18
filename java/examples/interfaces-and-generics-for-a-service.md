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



