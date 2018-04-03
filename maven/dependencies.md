# Dependency management

This is already covered in the Maven documentation and many tutorials.

Some rules:

* Never use snapshots in releases
* Ensure version convergence

## Version management

Handling dependencies includes controlling the versions of those dependencies. Maven allows doing so without actually including the versions into the project.

This is handled with the [dependency management][maven_dependency_management] and [plugin management][maven_plugin_management] options.

This way if the dependencies are added into any kind of children POM the version is already set by default. Which is very useful when creating base POMs or working with multi-module projects.

## Snapshots

Development releases are snapshots. These are handled by adding the -SNAPSHOT suffix to a version in the POM:

```
<version>1.2.3-SNAPSHOT</version>
```

The generated JAR will be timestamped, and can be stored into a repository like any dependency.

When using the snapshot version as a dependency Maven will download the latest snapshot.

```
<dependency>
   <groupId>groupId</groupId>
   <artifactId>artifactId</artifactId>
   <version>1.2.3-SNAPSHOT</version>
</dependency>
```

## Bill of Materials (BOM)

A BOM project just contains a POM with a set of dependencies. This allows enforcing a predefined configuration which reduces the problems caused by complex dependencies.

They can be used through the dependency management configuration:

```
<dependencyManagement>
   <dependencies>
      <dependency>
         <!-- Spring Framework BOM -->
         <groupId>org.springframework</groupId>
         <artifactId>spring-framework-bom</artifactId>
         <version>${spring.version}</version>
         <type>pom</type>
         <scope>import</scope>
      </dependency>
   </dependencies>
</dependencyManagement>
```

## Checking for updates

To check if there are newer versions for the dependencies use the following command:

```
mvn versions:display-dependency-updates versions:display-plugin-updates
```

[maven_dependency_management]: https://maven.apache.org/guides/introduction/introduction-to-dependency-mechanism.html#Dependency_Management
[maven_plugin_management]: https://maven.apache.org/pom.html#Plugin_Management
