# gitignore

The [git ignore file](https://git-scm.com/docs/gitignore) marks all the files and folders to be ignored by git. These won't be persisted.

This way generated content, such as test results or IDE configuration, won't be stored.

Just add files and folders to the file:

```text
# Eclipse files #
.buildpath
.classpath
.settings/
```

## Repository Folder

Always ignore the git folder:

```text
# Git folder #
/.git/
```

