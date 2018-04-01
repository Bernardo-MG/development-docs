# POMs

## Parent POM

Common configuration for multiple projects should be kept inside a parent POM.

These are handled just like any other dependency, and used by adding the following lines:

```
<parent>
   <groupId>com.bernardomg.maven</groupId>
   <artifactId>base-pom</artifactId>
   <version>1.2.0</version>
</parent>
```

Any project can use a parent POM. This is not a feature exclusive to multimodule projects.

A parent POM can keep common configuration for multiple projects:
- Dependency and plugin versions (plugin/dependency management nodes)
- Dependency and plugin dependencies, but only the bare minimum (plugin/dependency nodes)
- Profiles, for things such as deployment or testing

## Prepared POMs

There are a few parent POMs ready to use:
* [Base POM][base_pom], generic and useful for most projects
* [Archetype POM][archetype_pom], for Maven Archetypes

[archetype_pom]: https://github.com/Bernardo-MG/archetype-pom
[base_pom]: https://github.com/Bernardo-MG/base-pom
