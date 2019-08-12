# Request Path Testing

## Path Variable

This will use the "/path/code" URL

```java
mockMvc.perform(get("/path/{id}", "code"))
```

## **Query Parameters**

This will use the "/path?id=code" URL

```java
mockMvc.perform(get("/path").param("id", "code"))
```



