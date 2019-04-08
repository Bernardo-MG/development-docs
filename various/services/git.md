# git

Recommended version control tool.

## Configuration files

Projects include a .gitignore and a .gitattributes files.

### .gitignore

The [git ignore file](https://git-scm.com/docs/gitignore) marks all the files and folders to be ignored by git. These won't be persisted.

This way generated content, such as test results or IDE configuration, won't be stored.

Just add files and folders to the file:

```text
# Eclipse files #
.buildpath
.classpath
.settings/
```

### .gitattributes

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

### Line endings

Line endings can give lots of problems when working in a team. Always normalize them.

* [Github's Dealing with File Endings](https://help.github.com/articles/dealing-with-line-endings/)

### Sample files

These files include the recommended configurations:

* [Github's git ignore file examples](https://github.com/github/gitignore)
* [Various git attributes file examples](https://github.com/alexkaratarakis/gitattributes)

## Git flow

The most popular methodology for using git is [git flow](http://nvie.com/posts/a-successful-git-branching-model/).

