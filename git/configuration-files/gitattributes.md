# gitattributes

The [git attributes file](https://git-scm.com/docs/gitattributes) maps file extensions to content types. This way, for example, it is possible telling git that the xml extension is used only for text files and never for binaries.

Actually it is more like a set of hints than a configuration file, and can make it easier working with several formats.

```text
# Known text files
*.css           text diff=css
*.java          text diff=java eol=crlf
*.js            text eol=crlf
*.json          text
```

The previous example is mapping several extensions as text files. But it is also telling how to inspect changes, and which end of line character should be used.

This is saying that changes in CSS files should be inspected using CSS rules:

```text
*.css           text diff=css
```

This is setting up the end of line conversion for Javascript files to CRLF:

```text
*.js            text eol=crlf
```

It can contain global configuration too.

This defaults all files to text files, and normalizes line endings:

```text
text=auto
```

## Line endings

Line endings can give lots of problems when working in a team. Always normalize them.

* [Github's Dealing with File Endings](https://help.github.com/articles/dealing-with-line-endings/)

