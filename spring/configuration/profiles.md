# Profiles

## Configuration Classes

Classes and methods can be annotated to require a profile. If the profile is not set then they are not loaded.

```java
@Configuration
@Profile("profileName")
public class ConfigClass
```

## XML

```markup
<beans profile="profileName">
   <bean id="profiledBean" class="org.path.ClassName" />
</beans>
```

