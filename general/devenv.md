# Development environment

Setting up an usable environment is the first step when begginning to work, but it does not stop once the IDE is running and the code starts to be coded.

The environment is dependant of the technology being used, and may require setting up servers, or registering into third party services. But it always follows a similar pattern.

![Generic development environment][devenv_general]

The usual components of any development environment are:

- IDE, such as Eclipse or Pycharm
- Version control system, such as svn or git
- Code repository, such as GitHub or Bitbucket
- Project or dependencies management tool, such as Maven, npm, webpack, or pip
- Continuous integration service, such as Travis or Jenkins
- Dependencies repository, such as Bintray, PyPi or Nexus
- Documentation server, hosting files generated with Maven Site or Sphinx
- Reporting services, such as Coveralls

These are just the components which take a direct part in the project lifecycle. A few other important components, such as issues tracking, or test runners, are not included, but they will be touched in their own sections.

When analysing the development environment the first place to look at is the IDE, as it will be the main interface for the developer. This should be able to integrate with the other components and services, the most important being the version control system.

[devenv_general]: ../img/diagram/devenv_general.png
