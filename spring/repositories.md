---
description: Spring JPA Repositories
---

# Repositories

Spring offers a Repository interface for implementing the repository pattern.

In most cases these repositories will work without the need of a concrete implementation, Spring will generate the final repository from the interface.

```java
public interface EntityRepository extends JpaRepository<Entity, EntityKey> {

}
```

In this case the interface used is an extension specific for JPA.

## Setting Up Repositories

Repositories need to be loaded through an specific configuration:

```java
<jpa:repositories base-package="com.project.**.repository" />
```

This can be done with configuration classes:

```java
@EnableJpaRepositories
class Config {}
```

## Custom Queries

Spring can generate queries from the interface methods.

This will create a query for fetching all the entities with a specific name:

```java
public interface EntityRepository extends JpaRepository<Entity, EntityKey> {

   public Iterable<Entity> findByName(final String name);

}
```

## JPQL Queries

It is possible to define the query which a method will use:

```java
@Query("SELECT e FROM Entity e WHERE e.name = :name")
public Iterable<Entity> findByNameJpql(@Param("name") final String name);
```

Notice that it is using a named argument.

## Sorting and Paging

If a method receives a Sort or Pageable parameter it will be applied to the query.

## Custom Repositories

Repositores can be extended with custom code. This requires the following classes:

* Spring repository interface
* Custom repository interface
* Custom repository implementation

```java
public interface EntityRepository extends JpaRepository<Entity, EntityKey> extends EntityCustomRepository {

}

public interface EntityCustomRepository  {

   public Iterable<Entity> findByCustomQuery();

}


public class EntityCustomRepositoryImpl implements EntityCustomRepository   {

   public final Iterable<Entity> findByCustomQuery() {
      // Implementation
   }

}
```

Now calling the findByCustomQuery method in the repository will call the method in theDefautlEntityCustomRepository implementation. Spring will mix this code with the repository it generates.

```java
public final class EntityService {

   @Autowired
   private EntityRepository repository;

   public final Iterable<Entity> getByCustomQuery(){
      return repository.findByCustomQuery();
   }

}
```

## More Information

* [Working with Spring Data Repositories](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/#repositories)



