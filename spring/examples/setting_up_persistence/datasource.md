# Common Persistence Beans

## DB Access From Properties

```xml
<!-- Data source -->
<bean id="dataSource" class="${jdbc.dataSource.class}">
   <property name="driverClassName" value="${jdbc.driver}" />
   <property name="jdbcUrl" value="${jdbc.url}" />
   <property name="username" value="${jdbc.username}" />
   <property name="password" value="${jdbc.password}" />
</bean>
```

## DB Access From Environment

In this case the DB URI is taken from the DATABASE_URL environmental variable.

```xml
<!-- DB Access URI -->
<bean class="java.net.URI" id="dbUrl">
   <constructor-arg value="#{systemEnvironment['DATABASE_URL']}" />
</bean>

<!-- Data source -->
<bean id="dataSource" class="${jdbc.datasource.class}">
   <property name="driverClassName" value="${jdbc.driver}" />
   <property name="jdbcUrl"
      value="#{ 'jdbc:postgresql://' + @dbUrl.getHost() + ':' + @dbUrl.getPort() + @dbUrl.getPath() }" />
   <property name="username" value="#{ @dbUrl.getUserInfo().split(':')[0] }" />
   <property name="password" value="#{ @dbUrl.getUserInfo().split(':')[1] }" />
</bean>
```

## Common

```properties
# Bean classes
jpa.entityManagerFactory.class=org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean
```
