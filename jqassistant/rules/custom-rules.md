# Custom Rules

Custom rules are added as files to the jqassistant folder, in the project's root. They may be XML of AsciiDoc files.

Any group they define may be used by the project.

For example having the jqassistant\architecture.xml file, with this group:

```markup
<group id="architecture:Default">
   <includeConstraint refId="architecture:NoFacadeWithoutTransactional" />
</group>
```

This can be registered by the plugin:

```markup
<plugin>
   <!-- JQAssistant -->
   <!-- Architecture analysis tool. -->
   <groupId>com.buschmais.jqassistant</groupId>
   <artifactId>jqassistant-maven-plugin</artifactId>
   <executions>
      <execution>
         <id>validate-custom</id>
         <goals>
            <goal>analyze</goal>
         </goals>
         <configuration>
            <groups>
               <group>architecture:Default</group>
            </groups>
         </configuration>
      </execution>
   </executions>
</plugin>
```

