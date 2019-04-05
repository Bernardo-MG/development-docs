# Dynamic Dependency

A bean which will choose between two from the context and return one of them:

```java
@Bean
@Primary
@DependsOn({ "componentA", "componentB" })
public Component mainComponent(){
   // Picks between component A and component B
}

@Bean
public Component componentA(){
   // ...
}

@Bean
public Component componentB(){
// ...
}
```



