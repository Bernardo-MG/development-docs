# Common Persistence Beans

The persistence context requires the following common beans:

```xml
<!-- Transaction manager -->
<bean id="transactionManager" class="${jpa.transactionManager.class}">
   <property name="entityManagerFactory" ref="entityManagerFactory" />
</bean>

<!-- Entity manager -->
<bean id="entityManager" class="${jpa.entityManager.class}">
   <property name="entityManagerFactory" ref="entityManagerFactory" />
</bean>
```

```properties
# Bean classes
jpa.entityManagerFactory.class=org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean
jpa.entityManager.class=org.springframework.orm.jpa.support.SharedEntityManagerBean
jpa.adapter.class=
jpa.transactionManager.class=org.springframework.orm.jpa.JpaTransactionManager

# JPA configuration
jpa.persistenceUnitName=jpa_example
jpa.showSql=false
jpa.packagesToScan=com.bernardomg.example.jpa.model.collection,com.bernardomg.example.jpa.model.converter,com.bernardomg.example.jpa.model.embedded,com.bernardomg.example.jpa.model.enumeration,com.bernardomg.example.jpa.model.inheritance,com.bernardomg.example.jpa.model.key,com.bernardomg.example.jpa.model.relation,com.bernardomg.example.jpa.model.simple,com.bernardomg.example.jpa.model.table
```
