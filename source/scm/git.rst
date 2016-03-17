===
Git
===

Version control will be handled through Git, which allows creating local
repositories, and branching the development procedure.

Branches
========

All the projects will have at least two brances: the master and the development
branches.

The master branch will contain the latest stable release, while the development
one will store the latest version under development.

Additional branches may be created to keep track of features being developed.

Take a look at `A successful Git branching model`_ for a small and good guide
about this usage model.

Merging
=======

When merging to the master branch a new branch should be created just for this
purpose. It will be used to prepare the code, mostly setting the version
from snapshot to release, and then, after the merge, it will be removed.

The merge branches should not be used for anything else than temporal storage
of the code to be merged.

Git ignore
==========

Not all files should be persisted in the SCM, some, mostly generated files and
IDE configuration files, should be ignored. For this a file called .gitignore is
used.

- :download:`Java Git ignore file <../_downloads/git/java/.gitignore>`

Git attributes
==============

The Git attributes files sets up various paths for git.

- :download:`Java Git attributes file <../_downloads/git/java/.gitattributes>`


.. _A successful Git branching model: https://travis-ci.org/
