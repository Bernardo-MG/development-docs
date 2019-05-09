# Maven Plugin

To set it up:

```markup
<plugin>
   <!-- JQAssistant -->
   <!-- Architecture analysis tool. -->
   <groupId>com.buschmais.jqassistant</groupId>
   <artifactId>jqassistant-maven-plugin</artifactId>
   <executions>
      <execution>
         <id>jqassistant-scan</id>
         <goals>
            <goal>scan</goal>
         </goals>
      </execution>
      <execution>
         <id>validate-spring-boot</id>
         <goals>
            <goal>analyze</goal>
         </goals>
         <configuration>
            <groups>
               <group>spring-boot:Strict</group>
            </groups>
            <warnOnSeverity>MINOR</warnOnSeverity>
            <failOnSeverity>MAJOR</failOnSeverity>
            <rule>
               <defaultConceptSeverity>INFO</defaultConceptSeverity>
            </rule>
         </configuration>
      </execution>
   </executions>
</plugin>
```

To set up reporting:

```markup
<plugin>
   <!-- JQAssistant -->
   <!-- Architecture analysis tool. -->
   <groupId>com.buschmais.jqassistant</groupId>
   <artifactId>jqassistant-maven-plugin</artifactId>
   <reportSets>
      <reportSet>
         <reports>
            <report>report</report>
         </reports>
      </reportSet>
   </reportSets>
</plugin>
```

## Usage

Just run the integration tests:

```bash
mvn clean verify
```

Or the plugin commands \(this will require additional configuration to load the groups\):

```text
mvn jqassistant:scan jqassistant:analyze
```

Once it has finished you can start a local client for checking the analysis:

```bash
mvn jqassistant:server
```

The server will be available at [http://localhost:7474](http://localhost:7474)

