# Supplier

Receives no argument but returns an object. Can be used as a strategy for initialization.

```java
Supplier<String> supplier;
String result;

// Supplier initialization is skipped

result = supplier.get();
```

## Mapping Constructors

Suppliers can be created from default constructors easily:

```java
Supplier<Entity> supplier;

supplier = Entity::new;

// Both lines create a new entity the same way
Entity ent1 = new Entity();
Entity ent2 = supplier.get();
```



