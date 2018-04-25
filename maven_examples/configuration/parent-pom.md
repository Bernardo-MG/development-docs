# Parent POM

Use a parent POM to hold the configuration required by all the projects. You may use a hierarchy of POMs, but better avoid those complexities, instead prepare a flat POM with a broad configuration which covers most cases.

The few projects which will require a specialized POM are those requiring a very specific set of plugins or dependencies. For example when working with Maven archetypes you will need a different POM, but a project which creates a JAR can use the same POM as another which creates a WAR. Each project will include the changes they need.

## Example

These are a few parent POMs ready to use:

* [Base POM](https://github.com/Bernardo-MG/base-pom), generic and useful for most projects
* [Archetype POM](https://github.com/Bernardo-MG/archetype-pom), for Maven Archetypes



