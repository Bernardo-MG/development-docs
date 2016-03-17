=============
Maven plugins
=============

Maven can be customized with the help of several plugins. This is a list of
some of the ones used in the projects.

- Surefire, for unit tests
- Failsafe, for integration tests
- JaCoCo, for test coverage reports
- Enforcer, for setting up build rules
- Changes, for creating a changes list
- Checkstyle, for coding style validation
- Findbugs, for finding potential errors
- PMD, for checking the code quality

Build and report plugins
========================

Plugins can be used for the build or report concerns. The difference is basically
that the first ones are run during the project lifecycle, while the second ones
will generate a report for the Maven site.

Some plugins appear in both groups, and will run and generate a report based on
the results.
