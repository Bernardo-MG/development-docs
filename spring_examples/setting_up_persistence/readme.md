---
description: Setting Up Persistence with Spring
---

# Setting Up Persistence

The persistence context requires the following common beans:

```xml
<!-- Data source -->
<bean id="dataSource" class="${jdbc.dataSource.class}">
   <property name="driverClassName" value="${jdbc.driver}" />
   <property name="jdbcUrl" value="${jdbc.url}" />
   <property name="username" value="${jdbc.username}" />
   <property name="password" value="${jdbc.password}" />
</bean>

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
jdbc.dataSource.class=com.zaxxer.hikari.HikariDataSource

# JPA configuration
jpa.persistenceUnitName=jpa_example
jpa.showSql=false
jpa.packagesToScan=com.bernardomg.example.jpa.model.collection,com.bernardomg.example.jpa.model.converter,com.bernardomg.example.jpa.model.embedded,com.bernardomg.example.jpa.model.enumeration,com.bernardomg.example.jpa.model.inheritance,com.bernardomg.example.jpa.model.key,com.bernardomg.example.jpa.model.relation,com.bernardomg.example.jpa.model.simple,com.bernardomg.example.jpa.model.table
```

## Hibernate

```xml
<!-- JPA EntityManagerFactory -->
<bean id="entityManagerFactory" class="${jpa.entityManagerFactory.class}">
   <property name="jpaVendorAdapter" ref="jpaAdapter" />
   <property name="dataSource" ref="dataSource" />
   <property name="persistenceUnitName" value="${jpa.persistenceUnitName}" />
   <property name="packagesToScan" value="${jpa.packagesToScan}" />
   <property name="jpaProperties" ref="jpaProperties" />
</bean>

<!-- JPA Adapter -->
<bean id="jpaAdapter" class="${jpa.adapter.class}">
   <property name="database" value="${jpa.database}" />
   <property name="showSql" value="${jpa.showSql}" />
</bean>

<!-- JPA Properties -->
<util:map id="jpaProperties">
   <entry key="hibernate.dialect" value="${hibernate.dialect}" />
   <entry key="hibernate.hbm2ddl.auto" value="${hibernate.hbm2ddl.auto}" />
   <entry key="hibernate.ejb.naming_strategy" value="${hibernate.namingStrategy}" />
   <entry key="hibernate.show_sql" value="${jpa.showSql}" />
   <entry key="hibernate.format_sql" value="${hibernate.format_sql}" />
   <entry key="hibernate.cache.use_second_level_cache" value="${hibernate.cache.use_second_level_cache}" />
   <entry key="hibernate.cache.use_query_cache" value="${hibernate.cache.use_query_cache}" />
   <entry key="hibernate.cache.region.factory_class" value="${hibernate.cache.region.factory_class}" />
</util:map>
```

```
# Entity manager
jpa.adapter.class=org.springframework.orm.jpa.vendor.HibernateJpaVendorAdapter

# JPA configuration
jpa.showSql=true

# Hibernate Configuration
hibernate.hbm2ddl.auto=none
hibernate.namingStrategy=org.hibernate.cfg.ImprovedNamingStrategy
hibernate.format_sql=true
hibernate.cache.use_second_level_cache=true
hibernate.cache.use_query_cache=true
hibernate.cache.region.factory_class=org.hibernate.cache.ehcache.SingletonEhCacheRegionFactory
```

## EclipseLink

```xml
<!-- JPA EntityManagerFactory -->
<bean id="entityManagerFactory" class="${jpa.entityManagerFactory.class}">
   <property name="jpaVendorAdapter" ref="jpaAdapter" />
   <property name="dataSource" ref="dataSource" />
   <property name="persistenceUnitName" value="${jpa.persistenceUnitName}" />
   <property name="packagesToScan" value="${jpa.packagesToScan}" />
   <property name="jpaProperties" ref="jpaProperties" />
   <property name="loadTimeWeaver" ref="loadTimeWeaver" />
</bean>

<!-- Load time weaver -->
<bean id="loadTimeWeaver" class="${jpa.loadTimeWeaver.class}" />

<!-- JPA Adapter -->
<bean id="jpaAdapter" class="${jpa.adapter.class}">
   <property name="database" value="${jpa.database}" />
   <property name="showSql" value="${jpa.showSql}" />
</bean>

<!-- JPA Properties -->
<util:map id="jpaProperties">
   <entry key="eclipselink.cache.shared.default" value="${eclipselink.cache.shared.default}" />
   <entry key="eclipselink.weaving" value="${eclipselink.weaving}" />
   <entry key="eclipselink.ddl-generation" value="${eclipselink.ddl-generation}" />
   <entry key="eclipselink.ddl-generation.output-mode" value="${eclipselink.ddl-generation.output-mode}" />
   <entry key="eclipselink.allow-zero-id" value="${eclipselink.allow-zero-id}" />
   <entry key="eclipselink.id-validation" value="${eclipselink.id-validation}" />
</util:map>
```

```
# Entity manager
jpa.loadTimeWeaver.class=org.springframework.instrument.classloading.InstrumentationLoadTimeWeaver
jpa.adapter.class=org.springframework.orm.jpa.vendor.EclipseLinkJpaVendorAdapter

# JPA configuration
jpa.showSql=true

# Eclipselink Configuration
eclipselink.cache.shared.default=false
eclipselink.weaving=false
eclipselink.ddl-generation=none
eclipselink.ddl-generation.output-mode=database
eclipselink.allow-zero-id=true
eclipselink.id-validation=NEGATIVE
```



