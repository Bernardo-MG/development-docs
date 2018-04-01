# Maven Site

Maven supports its own documentation generation tool, the [Maven site][maven_site]. Which handled through the plugin of the same name.

To keep the project self contained, and take full advantage of Maven, it is recommended using this for generating the project's documentation.

## Site theme

By default the site is generated using an ugly and obsolete UI. For that reason the [docs Maven skin][docs_maven_skin] is used. With this theme the generated site becomes an HTML5 mobile-friendly page.

## Reports

The site includes not only documentation, but also several reports, generated along the docs.

## Command

As some reports will require the output from the tests it is recommended running all the tests before generating the site:

```
mvn verify site
```

[docs_maven_skin]: https://github.com/Bernardo-MG/docs-maven-skin
[maven_site]: https://maven.apache.org/plugins/maven-site-plugin/
