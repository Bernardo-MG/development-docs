# Continuous Integration

The CI service will take care of validating the changes, building/publishing artifacts and messaging services. This should be done after each commit to the code repository.

## Worflow

![CI flow][ci_flow]

CI is triggered by changes to the code repository.

But not all the changes should be treated equally, instead there are a few workflows depending on the source of the changes:

- Releases, when the code is for a version which will be published
- Development, for the main development version
- Pull request, when combining branches
- Other, for example when developing a feature

Releases and development versions are the primary source code bases for the project. And these receive special care, which usually includes deploying documentation.

Pull requests are fast, and will skip all special conditions. A pull request into the master branch should not publish the project, for example. If the pull request is accepted then a new workflow will start, and take care of any task needed.

Other triggers usually skip only the deployment tasks.

### Conditions

Flow | Marked by
--- | ---
Release | Comes from the master branch
Development | Comes from the develop branch
Pull request | Environment variable

### Publication flow

![Publish flow][publish_flow]

## Scripts

There is a set of [CI scripts][scripts_repo] to help running the CI tasks. These are meant for Travis and may not work with other services.

To use them copy the entire repository and set the access permissions, as the scripts readme explains.

```
before_install:
  # Gets scripts
  - git clone -b v1.1.2 --single-branch https://github.com/Bernardo-MG/ci-shell-scripts.git ~/.scripts
  # Sets scripts as executable
  - chmod -R +x ~/.scripts/*
```

### Setting up the environment

One of the scripts is run in most of the projects:

```
before_install:
  # Prepares CI environment
  - source ~/.scripts/travis/load-travis-environment.sh
```

This takes care of setting up a set of environment variables to be used by the other scripts.

It will create the following flow control environmental variables:

Variable | Type
--- | ---
DO\_DEPLOY | boolean
DO\_DEPLOY\_RELEASE | boolean
DO\_DEPLOY\_DEVELOP | boolean
DO\_DEPLOY\_DOCS | boolean
DO\_DEPLOY\_DOCS_RELEASE | boolean
DO\_DEPLOY\_DOCS_DEVELOP | boolean
DO\_TEST\_DOCS | boolean
DO\_COVERAGE | boolean

[ci_flow]: ../img/diagram/ci_general_activity.png
[publish_flow]: ../img/diagram/ci_publish_flow.png
[scripts_repo]: https://github.com/Bernardo-MG/ci-shell-scripts
