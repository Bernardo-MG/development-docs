=======
Testing
=======

All code should be tested when possible. While I tend to test as much as
possible, actually it is only required making sure that the main logic of
the project works as possible.

Unit tests
==========

Unit test check that a piece of logic works as expected. These should check
just a small piece of code, isolated from everything else.

There are several reasons for this isolation. First of all, as said a unit
test should just verify that a small piece of code is working, and if there
are dependencies the tests risks becoming a tests for those dependencies and
their effect on the code.

Also a unit test should run as fast as possible, to be executed after any
important change.

For this reason database tests, tests requiring a running server or in general
any test running something not directly under control of the test, and the
developer, are not unit tests.

Integration tests
=================

Integration tests make sure that several pieces of logic work together as expected.

An integration test may validate that a web application handles requests correctly,
or that the repositories work correctly with various kinds of databases.

This can make these tests big and slow, meaning they will run less often, usually
through a continuous integration service. But also their size and complexity means
that they may end giving false failures, if the dependencies are not working but
the tested code is.

Validity of tests
=================

While it can be hard knowing when a test is actually useful or not, there are
some guidelines to understand them.

First of all, the success of all tests does not mean that everything is working
as expected, at least not if these tests are not valid. And the failure of a
tests does not always mean that something broke.

Usually, if a unit test fails it means something broke in the application. If
an integration test fails it may mean that a dependency failed, not the test
itself.

Tests and releases
==================

The tests check the validity of the code up to the release, after that they are
no longer required, and should not be included in the final project.

For this reason the testing code and the actual code of the application should
be kept separated, the code to be released should be isolated from the tests,
and the tests should be easy to remove.

Usually this is achieved by having a source folder and a testing folder, but
there the actual way to achieve this will depend on the language and frameworks
used.
