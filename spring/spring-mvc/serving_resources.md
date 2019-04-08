# Serving Resources

## Context

The following will map into the /static path all the contents from the src/main/webapp/resources folder:

```markup
<mvc:resources mapping="/static/**" location="/resources/">
   <mvc:cache-control cache-public="true" max-age="2592000" />
</mvc:resources>
```

```java
public class WebConfiguration extends WebMvcConfigurerAdapter {

   @Override
   public void addResourceHandlers(final ResourceHandlerRegistry registry) {
      registry.addResourceHandler("/static/**").addResourceLocations("/resources/").setCachePeriod(2592000);
   }

}
```

If using webjars, this will add the libraries contents too:

```markup
<mvc:resources mapping="/static/**" location="/webjars/, /resources/">
   <mvc:cache-control cache-public="true" max-age="2592000" />
   <mvc:resource-chain resource-cache="true">
      <mvc:resolvers>
         <ref bean="webjarsResolver" />
      </mvc:resolvers>
   </mvc:resource-chain>
</mvc:resources>
```

