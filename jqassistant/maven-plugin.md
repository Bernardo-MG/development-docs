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
               <group>junit4:Strict</group>
               <group>spring-boot:Strict</group>
            </groups>
            <concepts>
               <concept>ejb3:*</concept>
               <concept>java:*</concept>
               <concept>java8:*</concept>
               <concept>jaxrs:*</concept>
               <concept>jpa2:*</concept>
               <concept>junit:*</concept>
               <concept>junit4:*</concept>
               <concept>osgi-bundle:*</concept>
               <concept>spring-boot:*</concept>
               <concept>spring-component:*</concept>
               <concept>spring-data:*</concept>
               <concept>spring-injection:*</concept>
               <concept>spring-transaction:*</concept>
            </concepts>
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

Or if you need to make use of advanced funciones remember to activate APOC:

```text
mvn jqassistant:server -Djqassistant.embedded.apocEnabled=true
```

The server will be available at [http://localhost:7474](http://localhost:7474)

