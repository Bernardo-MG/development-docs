# Open Graph

[Protocol used by Facebook](http://ogp.me/) to handle web pages meta data. The most clear use is allowing Facebook to create a small summary from a link.

This is done by adding meta tags to the header of an HTML page.

## Metadata Tags

The following tags are required:

```html
<!-- Facebook OpenGraph -->
<meta property="og:type" content="website"/>
<meta property="og:image" content="./static/favicon.png"/>
<meta property="og:url" content="http://docs.bernardomg.com/docs-bootstrap-template/"/>
<meta property="og:title" content="Index - Docs Bootstrap Template"/>
```

But this set adds more information:

```html
<!-- Facebook OpenGraph -->
<meta property="og:type" content="website"/>
<meta property="og:image" content="./static/favicon.png"/>
<meta property="og:url" content="http://docs.bernardomg.com/docs-bootstrap-template/"/>
<meta property="og:title" content="Index - Docs Bootstrap Template"/>
<meta property="og:site_name" content="Docs Bootstrap Template"/>
<meta property="og:description"
      content="Check the demo for the Docs Bootstrap Template, a modern template for documentation sites"/>
```
