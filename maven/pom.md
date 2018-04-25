# POMs

## Parent POM

Common configuration for multiple projects should be kept inside a parent POM.

These are handled just like any other dependency, and used by adding the following lines:

```xml
<parent>
   <groupId>com.bernardomg.maven</groupId>
   <artifactId>base-pom</artifactId>
   <version>1.2.0</version>
</parent>
```

Any project can use a parent POM. This is not a feature exclusive to multimodule projects.

A parent POM can keep common configuration for multiple projects:

* Dependency and plugin versions \(plugin/dependency management nodes\)
* Dependency and plugin dependencies, but only the bare minimum \(plugin/dependency nodes\)
* Profiles, for things such as deployment or testing

## Defaults

The [Maven Super POM](https://maven.apache.org/pom.html#The_Super_POM) includes several default properties.

### Array Properties

If a property contains several children they can be accessed as an array.

For example this gets the path to the first test resources directory:

```
${project.build.testResources[0].directory}
```



