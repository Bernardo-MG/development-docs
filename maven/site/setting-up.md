# Setting Up

Inside the POM:

```xml
<plugin>
    <!-- Site -->
    <!-- Generates the Maven Site -->
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-site-plugin</artifactId>
    <dependencies>
        <dependency>
            <!-- Docs Maven Skin -->
            <groupId>com.bernardomg.maven.skins</groupId>
            <artifactId>docs-maven-skin</artifactId>
            <version>${site.skin.version}</version>
        </dependency>
    </dependencies>
</plugin>
```

Inside /src/site/site.xml:

```xml
<skin>
   <groupId>com.bernardomg.maven.skins</groupId>
   <artifactId>docs-maven-skin</artifactId>
   <version>${site.skin.version}</version>
</skin>
```

Add an index file at src/site/markdown/index.md.

Then check any additional configuration which the skin may have.

## Aggregating Reports

This is for multimodule projects, where reports are generated for each module. These reports may be aggregated, but it is not recommended, as Maven has problems generating aggregated reports.

The way to activate aggregation for all reports is adding this property:

```xml
<properties>
   <aggregate>true</aggregate>
</properties>
```

### Plugins configuration

```xml
<plugin>
   <!-- Javadoc -->
   <!-- Handles the Javadocs. -->
   <groupId>org.apache.maven.plugins</groupId>
   <artifactId>maven-javadoc-plugin</artifactId>
   <executions>
      <execution>
         <id>aggregate-javadoc</id>
         <goals>
            <goal>aggregate</goal>
         </goals>
         <phase>site</phase>
      </execution>
   </executions>
</plugin>
```



