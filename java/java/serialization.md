---
description: Java Serialization
---

# Serialization

Serialization allows storing and persisting objects as bytes.

To activate serialization a class should be marked with the Serializable interface.

```java
public class SerializableClass implements Serializable
```

Now the class can be sent through a serializable medium:

```java
outputStream.writeObject(person);
```

## Transient Fields

Transient fields are not serialized:

```java
transient Blob bigField;
```

## Versioning

To handle several versions of the same serializable class add the serialVersionUID field:

```java
private static final long serialVersionUID = 1L;
```

