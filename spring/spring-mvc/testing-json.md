# Testing JSON

Using this:

```java
result = getMockMvc().perform(get);
```

## Print JSON

```java
result.andDo(MockMvcResultHandlers.print());
```

## Get JSON

```java
result.getResponse().getContentAsString();
```



