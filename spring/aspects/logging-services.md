# Logging Services

```java
@Aspect
public class ServiceLogger
{

   private static final Logger LOGGER = LoggerFactory.getLogger(ServiceLogger.class);

   public ServiceLogger()
   {
      super();
   }

   @AfterReturning(value = "execution(* es.seresco..*Service*.*(..)) && !bean(*Config) && !bean(*Factory)", returning = "returnValue")
   public void afterCall(JoinPoint joinPoint, Object returnValue)
   {
      LOGGER.debug("Called {} and returning {}", joinPoint.getSignature().toShortString(), returnValue);
   }

   @Before(value = "execution(* es.seresco..*Service*.*(..)) && !bean(*Config) && !bean(*Factory)", argNames = "joinPoint")
   public void beforeCall(JoinPoint joinPoint)
   {
      LOGGER.debug("Calling {} with arguments {}", joinPoint.getSignature().toShortString(), Arrays.asList(joinPoint.getArgs()));
   }

}
```

