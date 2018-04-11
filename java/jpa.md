---
description: JPA
---

# JPA

The JDK includes a persistence API, the JPA.

## Features

* Mapping persistence entities \(annotations or XML\)
* Query language \(DSL or domain objects\)

## Implementations

As it is an API, it requires an implementation. Some of the most popular are:

* [Hibernate](http://hibernate.org/)
* [Eclipselink](http://www.eclipse.org/eclipselink/)

## Example

To test and remember how to work with JPA use the [JPA Example](https://github.com/Bernardo-MG/jpa-example).

## API Version

There are several version of the Java Persistence API v2, which causes a lot of problems. But  luckily the version 2.2 of the API has an official release:

```xml
<dependency>
   <!-- JPA API -->
   <groupId>javax.persistence</groupId>
   <artifactId>javax.persistence-api</artifactId>
   <version>${javaee.api.version}</version>
</dependency>
```

Whenever possible use the version 2.2 or higher of JPA to avoid possible incompatibilities between API implementations.

## More Information

* [ObjectDB JPA Manual](https://www.objectdb.com/java/jpa)
