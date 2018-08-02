# Dependencies

## Bean Depends on Another

The bean "componentA" will be built after "componentB".

```java
@Bean
@DependsOn({ "componentB" })
public ComponentA componentA(){
   // ...
}

@Bean
public ComponentB componentB(){
   // ...
}
```



