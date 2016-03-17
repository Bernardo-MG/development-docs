======
Travis
======

`Travis`_ is a free continuous integration service, which supports
Github repositories.

It's very easy to set up, just requiring the use of a .travis.yml file, where
all the configuration and script execution is contained.

To avoid cluttering this with code a few scripts will be added, for such
jobs as publishing documentation or project artifacts.

Travis guide
============

The `Travis docs`_ are a good place to start learning about this service, and
explain how to set the CI environment for several languages.

Take a time to read it before going on with this guide.

Example Travis configuration file
=================================

As the docs explain, Travis requires a file to set up the CI environment.
Usually it is enough with having a generic one for each language, but sometimes
a project will require adapting it to its own needs.

These generic files can be found in the project templates, but are also included
here:

- :download:`Java basic configuration <../_downloads/travis/java/.travis.yml>`
- :download:`Python basic configuration <../_downloads/travis/python/.travis.yml>`

Note that these require scripts to be added to the project for them work correctly.

.. _Travis: https://travis-ci.org/
.. _Travis docs: https://docs.travis-ci.com/