---
description: JPA Entities
---

# JPA Entities

Java beans can be mapped to the database tables.

This can be done with XML or annotations.

## Constraints

* Usage of JPA annotations or XML mapping
* Non final classes
* Non final getters and setters

## Additional Constraints

These are recommended, but not compulsory:

* Extend the equals method
* Extend the hashCode method
* Extend the toString method

## Comparison Methods

For the equals and hashCode methods do not use the id for this, make use of the unique fields.

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

### Ids

Id columns are annotated with @Id:

```java
@Id
@GeneratedValue(strategy = GenerationType.IDENTITY)
@Column(name = "id", nullable = false, unique = true)
private Integer id = null;
```

When using composite ids these can be defined into a class id:

```java
@Entity(name = "CompositeKeyIdClassEntity")
@Table(name = "composite_key_idclass_entities")
@IdClass(CompositeKey.class)
public class CompositeKeyIdClassEntity implements Serializable {

    private static final long serialVersionUID = -4338241927428303803L;

    @Id
    @Column(name = "id1", nullable = false, unique = true)
    private Integer           id;

    @Id
    @Column(name = "id2", nullable = false, unique = true)
    private Long              supportId;

   // Constructor, getters, setters, etc...

}
```

This way they can be handled as a single object.

### Defining the Entity Name

By default JPA implementations will take the name of the class as the entity name. In this case the entity will be named SomeEntity.

```java
@Entity
@Table(name = "table")
public class SomeEntity
```

This can be changed by defining a name in the annotation. This will set the entity name as NamedEntity:

```java
@Entity(name = "NamedEntity")
@Table(name = "table")
public class SomeEntity
```

### Transient Fields

Any field containing data which should not be persisted has to be marked with the @Transient field. It is not recommended using this annotation, and it may be a hint telling that the entity is doing something else apart from storing persistent data.

## XML

## Additional Constraints

Requirementes may vary between implementations, but there are some recommended thinks to take care of:

* Avoid final classes
* Avoid final getters and setters for lazy fields

