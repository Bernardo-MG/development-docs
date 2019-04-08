# Dependency Management

This is already covered in the Maven documentation and many tutorials.

Some rules:

* Never use snapshots in releases
* Ensure version convergence

## Version Management

Handling dependencies includes controlling the versions of those dependencies. Maven allows doing so without actually including the versions into the project.

This is handled with the [dependency management](https://maven.apache.org/guides/introduction/introduction-to-dependency-mechanism.html#Dependency_Management) and [plugin management](https://maven.apache.org/pom.html#Plugin_Management) options.

This way if the dependencies are added into any kind of children POM the version is already set by default. Which is very useful when creating base POMs or working with multi-module projects.

## Snapshots

Development releases are snapshots. These are handled by adding the -SNAPSHOT suffix to a version in the POM:

```markup
<version>1.2.3-SNAPSHOT</version>
```

The generated JAR will be timestamped, and can be stored into a repository like any dependency.

When using the snapshot version as a dependency Maven will download the latest snapshot.

```markup
<dependency>
   <groupId>groupId</groupId>
   <artifactId>artifactId</artifactId>
   <version>1.2.3-SNAPSHOT</version>
</dependency>
```

## Bill of Materials \(BOM\)

A BOM project just contains a POM with a set of dependencies. This allows enforcing a predefined configuration which reduces the problems caused by complex dependencies.

They can be used through the dependency management configuration:

```markup
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

## Checking for Updates

To check if there are newer versions for the dependencies use the following command:

```bash
mvn versions:display-dependency-updates versions:display-plugin-updates
```

## Purging Dependencies

Sometimes you need to delete and download again all the dependencies. This may be caused by the use of snapshots.

This command will do so:

```text
mvn dependency:purge-local-repository
```

To remove only snapshots:

```text
mvn dependency:purge-local-repository -DsnapshotsOnly=true
```

