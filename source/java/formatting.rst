==========
Formatting
==========

All the Java code should be formatted prior to a release. It is recommended also
formatting before commiting a development version, but not required.

The Java conventions should be followed for this.

Eclipse formatter configuration
===============================

There is a configuration file prepared for using with the Eclipse formatter. This
can be downloaded below, but also can be found as a `gist on Github`_.

:download:`Eclipse Java formatter configuration <../_downloads/eclipse/java/Eclipse-Format.xml>`

Ordering the code
=================

All the methods and variables in a class should be ordered alphabetically, and grouped
by visibility.

The visibility order is:

- Public
- Private
- Protected
- Package

Eclipse by default won't do this, and the option "Sort all members" should be selected
when using the sort members command. Additionally, on the "members sort order"
section the "Sort members in same category by visibility" option should be
selected.

.. _gist on Github: https://travis-ci.org/
