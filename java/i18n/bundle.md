# Resource Bundle

Resource bundles contain a map with internationalized values, each identified by a text key.

A bundle will contain objects which change from one location to another, such as Strings or Images.

## Messages in a File

Bundles are usually loaded from properties files. The following example will load a MessagesBundle.properties file.

```java
Locale locale;
ResourceBundle messages;

locale = new Locale("fr", "CA", "UNIX");
messages = ResourceBundle.getBundle("MessagesBundle", locale);
```

This will contain the default messages, and additional languages can be added by extending the file name. To add a German bundle add a MessagesBundle\_de.properties file, and for a French one use MessagesBundle\_fr.properties.

The correct file will be loaded by checking the received locale, and falling back to the default file.

## Messages in a Class

Instead of using a file the messages may be stored inside a class.

```java
public class StatsBundle_fr_CA extends ListResourceBundle {

   private Object[][] contents = {
      { "message", "Translated message" }
   };

   public Object[][] getContents() {
      return contents;
   }

}
```

