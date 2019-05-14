# Extending Initialization

The BeanPostProcessor allows extending the initialization procedure.

For example it may be used to wrap components:

```java
public final class AdditionalSecurityBeanPostProcessor implements BeanPostProcessor
{

   public AdditionalSecurityBeanPostProcessor()
   {
      super();
   }

   @Override
   public final Object postProcessBeforeInitialization(final Object bean, final String beanName) throws BeansException
   {
      return bean;
   }

   @Override
   public final Object postProcessAfterInitialization(final Object bean, final String beanName) throws BeansException
   {
      if (bean instanceof SecurityComponent)
      {
         return new AdditionalSecurityComponentWrapper((SecurityComponent) bean);
      }

      return bean;
   }

}
```

