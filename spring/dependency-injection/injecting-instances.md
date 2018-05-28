# Injecting Multiple Instances

It is possible to inject all the instances of an interface or class:

```java
@Autowired(required = false)
public final void setInterceptors(final List<InterceptorBean> inters)
{
   interceptors = inters;
}
```

Generics will be taken into account. Meaning that InterceptorBean&lt;TypeA&gt; is not the same as InterceptorBean&lt;TypeB&gt;.



