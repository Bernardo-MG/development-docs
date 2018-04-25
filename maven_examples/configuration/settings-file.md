# Settings file

Sensitive information, such as authentication data, should be moved to a [Maven settings file](https://maven.apache.org/settings.html), located in a secure path.

Then it can be loaded by Maven with any command:

```bash
mvn deploy --settings ~/settings.xml
```



