---
description: Setting Up the Application
---

# Setting Up a Web Application

## web.xml

The application requires a web.xml file. If using Maven it should be located at src\main\webapp\WEB-INF\web.xml.

And should like this:

```markup
<?xml version="1.0" encoding="ISO-8859-1"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://java.sun.com/xml/ns/javaee"
   xsi:schemaLocation="http://java.sun.com/xml/ns/javaee
          http://java.sun.com/xml/ns/javaee/web-app_3_0.xsd"
   version="3.0" metadata-complete="true">

   <display-name>Spring MVC App</display-name>
   <description>A Spring MVC application</description>

   <context-param>
      <!-- Spring XML context -->
      <param-name>contextClass</param-name>
      <param-value>org.springframework.web.context.support.XmlWebApplicationContext</param-value>
   </context-param>

   <context-param>
      <!-- Spring XML configuration -->
      <param-name>contextConfigLocation</param-name>
      <param-value>classpath:context/application-context.xml</param-value>
   </context-param>

   <listener>
      <!-- Starts up and shuts down the context -->
      <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
   </listener>

   <servlet>
      <!-- Application servlet -->
      <servlet-name>appServlet</servlet-name>
      <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
      <init-param>
         <param-name>contextConfigLocation</param-name>
         <param-value>classpath:context/servlet.xml</param-value>
      </init-param>
      <load-on-startup>1</load-on-startup>
   </servlet>

   <servlet-mapping>
      <!-- Application servlet mapping -->
      <servlet-name>appServlet</servlet-name>
      <url-pattern>/</url-pattern>
   </servlet-mapping>

   <error-page>
      <error-code>404</error-code>
      <location>/404</location>
   </error-page>

</web-app>
```

## Application Context

The application context contains the horizontal concerns of the application.

This means that if the web application is split into smaller parts, all the common components will be in the application context.

The configuration would look like this:

```markup
<beans xmlns="http://www.springframework.org/schema/beans" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xmlns:context="http://www.springframework.org/schema/context" xmlns:jdbc="http://www.springframework.org/schema/jdbc"
   xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/jdbc
        http://www.springframework.org/schema/jdbc/spring-jdbc.xsd
        http://www.springframework.org/schema/context 
        http://www.springframework.org/schema/context/spring-context.xsd">

   <!-- Properties -->
   <context:property-placeholder
      location="classpath:config/persistence-@spring.profile.database@.properties, 
                   classpath:config/persistence-access.properties,
                   classpath:config/persistence.properties" />

   <!-- Imports -->
   <import resource="classpath:context/persistence.xml" />
   <import resource="classpath:context/persistence-versioning.xml" />

</beans>
```

Note the @spring.profile.database@. This is done to allow choosing the database when building the project with Maven.

## Servlet Context

Servlets are the smaller components of the application.

The context would look like this:

```markup
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xmlns:context="http://www.springframework.org/schema/context" xmlns:mvc="http://www.springframework.org/schema/mvc"
   xmlns="http://www.springframework.org/schema/beans" xmlns:util="http://www.springframework.org/schema/util"
   xsi:schemaLocation="http://www.springframework.org/schema/mvc
        http://www.springframework.org/schema/mvc/spring-mvc.xsd
        http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context
        http://www.springframework.org/schema/context/spring-context.xsd
        http://www.springframework.org/schema/util
        http://www.springframework.org/schema/util/spring-util.xsd">

   <!-- Imports -->
   <import resource="classpath:context/view.xml" />
   <import resource="classpath:context/service.xml" />
   <import resource="classpath:context/messages.xml" />
   <import resource="classpath:context/mvc.xml" />

   <!-- Properties -->
   <context:property-placeholder
      location="classpath:config/view.properties,
                   classpath:config/service.properties,
                   classpath:config/servlet.properties" />

   <!-- Scans for beans -->
   <context:component-scan base-package="com.bernardomg.example.spring.mvc.content" />


</beans>
```

The importan import here is the one defining the MVC configuration:

```markup
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xmlns:context="http://www.springframework.org/schema/context" xmlns:mvc="http://www.springframework.org/schema/mvc"
   xmlns="http://www.springframework.org/schema/beans" xmlns:util="http://www.springframework.org/schema/util"
   xsi:schemaLocation="http://www.springframework.org/schema/mvc
        http://www.springframework.org/schema/mvc/spring-mvc.xsd
        http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context
        http://www.springframework.org/schema/context/spring-context.xsd
        http://www.springframework.org/schema/util
        http://www.springframework.org/schema/util/spring-util.xsd">

   <!-- MVC configuration -->
   <mvc:annotation-driven conversion-service="conversionService"
      validator="validator">
   </mvc:annotation-driven>

   <!-- Static resources -->
   <mvc:resources mapping="/static/**" location="/webjars/, /resources/">
      <mvc:cache-control cache-public="true" max-age="2592000" />
      <mvc:resource-chain resource-cache="true">
         <mvc:resolvers>
            <ref bean="webjarsResolver" />
         </mvc:resolvers>
      </mvc:resource-chain>
   </mvc:resources>

   <bean id="webjarsResolver" class="${resolver.webjars.class}" />

   <mvc:default-servlet-handler />

   <bean id="conversionService" class="${conversion.service.class}"/>

   <bean id="validator" class="${validator.factory.class}">
      <property name="validationMessageSource" ref="messageSource" />
   </bean>

</beans>
```

