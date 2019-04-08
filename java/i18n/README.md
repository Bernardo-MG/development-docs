# Internationalization

The ResourceBundle class takes care of translations:

```java
ResourceBundle messages;

messages = ResourceBundle.getBundle("MessagesBundle");

messages.getString("greetings");
```

Remember that not only texts, but other things such as currencies or times, can require internationalization.

## More Information

* [Internationalization](https://docs.oracle.com/javase/tutorial/i18n/index.html)

