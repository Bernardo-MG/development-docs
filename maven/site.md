# Maven Site

Maven supports its own documentation generation tool, the [Maven site](https://maven.apache.org/plugins/maven-site-plugin/). Which handled through the plugin of the same name.

To keep the project self contained, and take full advantage of Maven, it is recommended using this for generating the project's documentation.

## Site Theme

By default the site is generated using an ugly and obsolete UI. For that reason the [docs Maven skin](https://github.com/Bernardo-MG/docs-maven-skin) is used. With this theme the generated site becomes an HTML5 mobile-friendly page.

## Reports

The [report plugins](./maven_reports.md) will generate several reports along the site. Check the plugin documentation to find about each of them, but most of them will generate a HTML file which can be linked by the site.

Usually these HTML files are processed by the Maven skin being used. But some reports will ignore that completely.

Remember that some of these reports may need additional information, for example the coverage data generated during the testing phase.

## Command

As some reports will require test results it is recommended running all the tests before generating the site:

```shell
mvn verify site
```

To generate a test version of the site, useful for multimodule projects:

```
mvn verify site site:stage
```



