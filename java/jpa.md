---
description: JPA
---

# JPA

Java Persistence API. An specification for persistence in Java.

There are several implementations. Among those the most important are:

* [Hibernate](http://hibernate.org/)
* [Eclipselink](http://www.eclipse.org/eclipselink/)

## Example

To test and remember how to work with JPA use the [JPA Example](https://github.com/Bernardo-MG/jpa-example).

## API dependency

There are several version of the Java Persistence API v2, which causes a lot of problems.

Luckily the version 2.2 of the API has an official release:

```
<dependency>
   <!-- JPA API -->
   <groupId>javax.persistence</groupId>
   <artifactId>javax.persistence-api</artifactId>
   <version>${javaee.api.version}</version>
</dependency>
```

Whenever possible use the version 2.2 or higher of JPA to avoid possible incompatibilities between API implementations.

