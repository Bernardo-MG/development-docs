---
description: JPA Entities
---

# JPA Entities

Java beans can be mapped to the database tables.

This can be done with XML or annotations.

## Additional Constraints

Always extend the equals and hashCode methods. This way if two entities contain the same data they can be handled as being the same entity.

It is recommended extending the toString method too, to make the resulting string readable.

## Annotations

```java
@Entity(name = "SimpleEntity")
@Table(name = "simple_entities")
public class SimpleEntity {

    /**
     * Entity's ID.
     */
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    @Column(name = "id", nullable = false, unique = true)
    private Integer           id               = null;

    /**
     * Name of the entity.
     */
    @Column(name = "name", nullable = false, unique = true)
    private String            name             = "";

    public SimpleEntity () {
        super();
    }

    @Override
    public final boolean equals(final Object obj) {
        if (this == obj) {
            return true;
        }

        if (obj == null) {
            return false;
        }

        if (getClass() != obj.getClass()) {
            return false;
        }

        final SimpleEntity other = (SimpleEntity ) obj;
        return Objects.equals(name, other.name);
    }

    @Override
    public final Integer getId() {
        return id;
    }

    @Override
    public final String getName() {
        return name;
    }

    @Override
    public final int hashCode() {
        return Objects.hash(name);
    }

    @Override
    public final void setId(final Integer identifier) {
        id = checkNotNull(identifier, "Received a null pointer as identifier");
    }

    @Override
    public final void setName(final String value) {
        name = checkNotNull(value, "Received a null pointer as name");
    }

    @Override
    public final String toString() {
        return MoreObjects.toStringHelper(this).add("name", name).toString();
    }

}
```

### Transient Fields

Any field containing data which should not be persisted has to be marked with the @Transient field. It is not recommended using this annotation, and it may be a hint telling that the entity is doing something else apart from storing persistent data.

## XML

## Additional Constraints

Requirementes may vary between implementations, but there are some recommended thinks to take care of:

* Avoid final classes
* Avoid final getters and setters for lazy fields



