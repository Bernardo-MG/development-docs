# Generating Metamodel

By using the Maven processor plugin, and the Hibernate JPA model generator, the metamodel classes will be generated in the same package as the entities.

```markup
<plugin>
   <!-- Maven processor -->
   <!-- Processes Java annotations -->
   <groupId>org.bsc.maven</groupId>
   <artifactId>maven-processor-plugin</artifactId>
   <version>${plugin.processor.version}</version>
   <executions>
      <execution>
         <id>generate-jpa-metamodel</id>
         <goals>
            <goal>process</goal>
         </goals>
         <configuration>
            <processors>
               <processor>org.hibernate.jpamodelgen.JPAMetaModelEntityProcessor</processor>
            </processors>
         </configuration>
      </execution>
   </executions>
   <dependencies>
      <dependency>
         <!-- Hibernate JPA model generator -->
         <!-- This is used to generate the metamodel -->
         <groupId>org.hibernate</groupId>
         <artifactId>hibernate-jpamodelgen</artifactId>
         <version>${hibernate.version}</version>
      </dependency>
   </dependencies>
</plugin>
```

They won't be added to the source code folders, but will be included in the target folder, and can be imported like any other dependency:

```java
import com.bernardomg.example.jpa.model.simple.DefaultSimpleEntity;
import com.bernardomg.example.jpa.model.simple.DefaultSimpleEntity_;
```

In this case DefaultSimpleEntity\_ is the metamodel for DefaultSimpleEntity.

