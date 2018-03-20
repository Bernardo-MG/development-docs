# Development ecosystem

Developing requires several services and applications. The choices to be made will depend on the technology used, and the requirements of the project, but there are some general guidelines.

![Generic development environment][dev_eco_general]

Most development environments will have:

Component|Usage|Example
---|---|---
Code repository|Store for the version control system, which allows several people to access and use it|Github, Bitbucket
Continuous integration|Service for handling tasks after changes are committed to a project|Travis, Jenkins
Dependencies management tool|Application which handles the project dependencies|Maven, npm, pip
Dependencies repository|Store with libraries and projects to be used as dependencies|Bintray, PyPi, Maven Repository
Documentation server|A server for files which document the project|Any static content server
IDE|Integrated Development Environment, comprehensive application to help programming|Eclipse, Pycharm
Packaging management tool|Application which handles the project building process|webpack
Project management tool|Application which handles the repetitive, complex and common tasks of project building|Maven
Reporting services|Service for generating any kind of report, such as code coverage or code quality|Coveralls, Landscape
Version control system|System which keeps track and a history of all the changes in code|svn, git

But these are just the components which take a direct part in the project lifecycle. A few other important components, such as issues tracking, or test runners, are not included and will be commented in their own sections.

[dev_eco_general]: ../img/diagram/dev_eco_general.png
