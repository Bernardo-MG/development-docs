# Archetypes

[Maven archetypes](https://maven.apache.org/guides/introduction/introduction-to-archetypes.html) can be used to create new projects fast.

* [Library Maven Archetype](https://github.com/Bernardo-MG/library-maven-archetype), meant for generic Java projects and libraries
* [Spring MVC with Thymeleaf Maven Archetype](https://github.com/Bernardo-MG/spring-mvc-thymeleaf-maven-archetype)

## Usage

Before using it an archetype should be downloaded from a repository. It works like any other dependency, but requires a repository with an archetypes catalog.

As an alternative it is always possible to install the archetype project locally before usage:

```bash
mvn install
```

## Setup

When creating a new archetype the [Maven Archetype Plugin](http://maven.apache.org/archetype/maven-archetype-plugin) should be added to the project.

