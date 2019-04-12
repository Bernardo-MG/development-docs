# Site

Maven supports its own documentation generation tool, the [Maven site](https://maven.apache.org/plugins/maven-site-plugin/). Which handled through the plugin of the same name.

To keep the project self contained, and take full advantage of Maven, it is recommended using this for generating the project's documentation.

## Command

As some reports will require test results it is recommended running all the tests before generating the site:

```bash
mvn verify site
```

To generate a test version of the site, useful for multimodule projects:

```bash
mvn verify site site:stage
```

