# Argument Resolvers

## Pagination

```java
mockMvc = MockMvcBuilders.standaloneSetup(getController())
        .setCustomArgumentResolvers(new PageableHandlerMethodArgumentResolver())
```
