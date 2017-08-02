# Development ecosystem

Setting up an usable architecture is the first step when begginning to work, but it does not stop once the IDE is running and the code starts to be coded.

The environment is dependant of the technology being used, and may require setting up servers, or registering into third party services. But it always follows a similar pattern.

![Generic development environment][dev_eco_general]

The usual components of any development environment are:

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

These are just the components which take a direct part in the project lifecycle. A few other important components, such as issues tracking, or test runners, are not included, but they will be touched in their own sections.

When analysing the development environment the first place to look at is the IDE, as it will be the main interface for the developer. This should be able to integrate with the other components and services, the most important being the version control system.

[dev_eco_general]: ../img/diagram/dev_eco_general.png
