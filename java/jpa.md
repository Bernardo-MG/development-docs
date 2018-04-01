# JPA

Java Persistence API. An specification for persistence in Java.

There are several implementations. Among those the most important are:

* [Hibernate][hibernate]
* [Eclipselink][eclipselink]

## Example

To test and remember how to work with JPA use the [JPA Example][jpa-example].

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

[hibernate]: http://hibernate.org/
[eclipselink]: http://www.eclipse.org/eclipselink/

[jpa-example]: https://github.com/Bernardo-MG/jpa-example
