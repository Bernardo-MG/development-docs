---
description: JPQL
---

# JPQL

With the Java Persistence Query Language the persistence objects graph can be queried, in a similar way to querying a database by using SQL, and it looks just like that.

```sql
SELECT c FROM Customer c JOIN c.orders o WHERE c.status = 1 AND o.totalPrice > 10000
```

## Values Placeholders

Queries can contain variables, which are swapped by actual values when executing the query.

In this example there is a variable named id:

```sql
SELECT entity FROM SimpleEntity entity WHERE entity.id = :id
```

## Executing queries

A query can be executed with a javax.persistence.EntityManager.

```java
String query = "SELECT entity FROM SimpleEntity entity WHERE entity.id = :id";
Query query = entityManager.createQuery(query);

query.setParameter("id", id);

// Returns the entity
query.getSingleResult();
```

## Integration

JPQL can be used by any JPA implementation, replacing other query languages.

### Differences Between Implementations

Note that some implementations may give problems with certain operations. Changing from one JPA provider to another, or switching from a JDBC to another may cause unexpected issues.

For example this query works with Eclipselink:

```sql
SELECT entity FROM CollectionEntity entity WHERE :value IN (entity.values)
```

But will fail with Hibernate, which requires this one:

```sql
SELECT entity FROM CollectionEntity entity WHERE :value IN ELEMENTS(entity.values)
```

## More Information

* [JPQL Language Reference](https://docs.oracle.com/html/E13946_01/ejb3_langref.html)
* [JPA Queries](https://www.objectdb.com/java/jpa/query)
* [Ultimate Guide to JPQL Queries with JPA and Hibernate](https://www.thoughts-on-java.org/jpql/)

