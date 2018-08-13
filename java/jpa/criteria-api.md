---
description: Criteria API
---

# Criteria API

In a similar way to JPQL, Criteria API gives tools for querying the persistence graph, but in this case by using objects instead of a DSL.

These queries are harder to read, but easier to modify dynamically.

## Creating a Query

This JPQL query:

```sql
SELECT entity FROM SimpleEntity entity WHERE entity.id = :id
```

Is equivalent to this:

```java
final CriteriaBuilder builder;                  // Builder
final CriteriaQuery<DefaultSimpleEntity> query; // Query
final Root<DefaultSimpleEntity> entity;         // Root entity

// Prepares the criteria API query
builder = entityManager.getCriteriaBuilder();
query = builder.createQuery(DefaultSimpleEntity.class);
entity = query.from(DefaultSimpleEntity.class);

// Generates a select query
query.select(entity);

// Queries the entities with the specified id
query.where(builder.equal(entity.get(DefaultSimpleEntity_.id), id));

// Returns the entity
query.getSingleResult();
```

## Metamodel

The DefaultSimpleEntity\_ is a class containing only metadata to be used by JPA, so when this constant is used:

```java
DefaultSimpleEntity_.id
```

It is making a reference to this metamodel field:

```java
public static volatile SingularAttribute<DefaultSimpleEntity, Integer> id;
```

Which describes this entity field:

```java
@Id
@GeneratedValue(strategy = GenerationType.IDENTITY)
@Column(name = "id", nullable = false, unique = true)
private Integer           id               = null;
```

The metamodel can be generated automatically from a persistence entity with the help of a project management tool. This way any change to the entity is always mirrored by the metamodel.

## More Information

* [Using the Criteria API to Create Queries](https://docs.oracle.com/javaee/6/tutorial/doc/gjitv.html)
* [Create type-safe queries with the JPA static metamodel](https://www.thoughts-on-java.org/jpa-21-entity-graph-part-2-define/)



