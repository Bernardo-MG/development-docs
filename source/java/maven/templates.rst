=========
Templates
=========

Maven offers project templates with the archetypes and the base POM.

Archetypes
==========

Currently there is only a single Maven Archetype being used, the `Library Maven Archetype`_,
which allows creating a new Maven project ready to start coding a new library.

Base POM
========

A base POM, just called the `base POM`_, is offered to quickly set up Maven
based projects. The Library Maven Archetype already makes use of it, and comes
ready for it.

For using it just add the following code to the POM. Note that the version indicated
here may not be the latest one.

.. code-block:: xml

    <parent>
        <groupId>com.wandrell.maven</groupId>
        <artifactId>base-pom</artifactId>
        <version>0.1.1</version>
    </parent>

.. _Library Maven Archetype: https://maven.apache.org/
.. _base POM: https://maven.apache.org/
