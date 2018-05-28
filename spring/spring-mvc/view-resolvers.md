# View Resolvers

These are used to handle and generate the UI.

```xml
<bean id="thymeleafViewResolver" class="${template.viewResolver.class}">
   <property name="templateEngine" ref="templateEngine" />
   <property name="order" value="2" />
   <property name="characterEncoding" value="UTF-8" />
</bean>
```

```java
@Bean
public ViewResolver getViewResolver(final SpringTemplateEngine templateEngine)
{
   final ThymeleafViewResolver viewResolver;

   viewResolver = new ThymeleafViewResolver();
   viewResolver.setTemplateEngine(templateEngine);
   viewResolver.setOrder(2);
   viewResolver.setViewNames(new String[] { "*.tpl" });

   return viewResolver;
}
```



