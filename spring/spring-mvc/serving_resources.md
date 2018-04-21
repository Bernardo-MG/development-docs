# Serving resources

## Context

The following will map into the /static path all the contents from the src/main/webapp/resources folder:

```xml
<mvc:resources mapping="/static/**" location="/resources/">
   <mvc:cache-control cache-public="true" max-age="2592000" />
</mvc:resources>
```

If using webjars, this will add the libraries contents too:

```xml
<mvc:resources mapping="/static/**" location="/webjars/, /resources/">
   <mvc:cache-control cache-public="true" max-age="2592000" />
   <mvc:resource-chain resource-cache="true">
      <mvc:resolvers>
         <ref bean="webjarsResolver" />
      </mvc:resolvers>
   </mvc:resource-chain>
</mvc:resources>
```
