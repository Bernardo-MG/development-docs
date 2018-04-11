---
description: JPQL
---

# JPQL

With the Java Persistence Query Language the persistence objects graph can be queried, in a similar way to querying a database by using SQL, and it looks just like that.

```
SELECT c FROM Customer c JOIN c.orders o WHERE c.status = 1 AND o.totalPrice > 10000
```

## Values Placeholders

Queries can contain variables, which are swapped by actual values when executing the query.

In this example there is a variable named value:

```
SELECT entity FROM EntityObject entity WHERE entity.field = :value
```

## Executing queries

A query can be executed with a javax.persistence.EntityManager.

```java
String query = "SELECT entity FROM EntityObject entity WHERE entity.field = :value";
Query query = entityManager.createQuery(query);

query.setParameter("value", value);

// Returns the result
query.getResultList();
```

## Integration

JPQL can be used by any JPA implementation, replacing other query languages.

### Differences Between Implementations

Note that some implementations may give problems with certain operations. Changing from one JPA provider to another, or switching from a JDBC to another may cause unexpected issues.

For example this query works with Eclipselink:

```
SELECT entity FROM CollectionEntity entity WHERE :value IN (entity.values)
```

But will fail with Hibernate, which requires this one:

```
SELECT entity FROM CollectionEntity entity WHERE :value IN ELEMENTS(entity.values)
```



