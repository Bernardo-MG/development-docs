# git

Recommended version control tool.

## Configuration files

Projects include a .gitignore and a .gitattributes files.

The first indicates all the files and folders which should not be persisted into the code repository, mostly to avoid saving generated content, test results or IDE configuration files.

The attributes file maps file extensions to content types, this way, for example, it is possible telling git that the xml extension is used only for text files and never for binaries.

### Sample files

These files include the recommended configurations:

* [Github's git ignore file examples][gitignore_github]
* [Various git attributes file examples][gitattributes_github]
* [Sample git attributes file][gitattributes]

[gitattributes]: ../download/git/.gitignore
[gitattributes_github]: https://github.com/alexkaratarakis/gitattributes
[gitignore_github]: https://github.com/github/gitignore
