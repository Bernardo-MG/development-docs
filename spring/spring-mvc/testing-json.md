# Testing JSON

Using this:

```java
result = getMockMvc().perform(get).andReturn();
```

## Print JSON

```java
result.andDo(MockMvcResultHandlers.print());
```

## Get JSON

```java
result.getResponse().getContentAsString();
```

## Check Number of Elements

```java
result.andExpect(MockMvcResultMatchers.jsonPath("$.content", Matchers.hasSize(1)));
```

## Check String

```java
result.andExpect(MockMvcResultMatchers.jsonPath("$.content", Matchers.equalTo("text")));
```



