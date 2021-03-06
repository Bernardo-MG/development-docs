# Continuous Integration

The CI service will take care of building, testing and deploying. Along any other repetitive task which the project may need.

It should run after each commit to the code repository, and take care of generating releases. Never depend on manual tasks for important jobs.

## Workflow

![](../.gitbook/assets/ci_general_activity.png)

CI is triggered by changes to the code repository.

But not all the changes should be treated equally, instead there are a few workflows depending on the source of the changes:

* Releases, when the code is for a version which will be published
* Development, for the main development version
* Pull request, when combining branches
* Other, for example when developing a feature

Releases and development versions are the primary source code bases for the project. And these receive special care, which usually includes deploying documentation.

Pull requests are fast, and will skip all special conditions. A pull request into the master branch should not publish the project, for example. If the pull request is accepted then a new workflow will start, and take care of any task needed.

Other triggers usually skip only the deployment tasks.

### Conditions

| Flow | Marked by |
| :--- | :--- |
| Release | Comes from the master branch |
| Development | Comes from the develop branch |
| Pull request | Environment variable |
| Other | Any other case |

### Tasks

| Flow | Marked by |
| :--- | :--- |
| Release | Validate project, publish release artifacts |
| Development | Validate project, publish development artifacts |
| Pull request | Validate project, forbid invalid merges |
| Other | Validate project |

### Publication flow

![](../.gitbook/assets/ci_publish_flow.png)

## Scripts

There is a set of [CI scripts](https://github.com/Bernardo-MG/ci-shell-scripts) to help running the CI tasks. These are meant for Travis and may not work with other services.

To use them copy the entire repository and set the access permissions, as the scripts readme explains.

```text
before_install:
  # Gets scripts
  - git clone -b v1.1.2 --single-branch https://github.com/Bernardo-MG/ci-shell-scripts.git ~/.scripts
  # Sets scripts as executable
  - chmod -R +x ~/.scripts/*
```

### Setting up the environment

One of the scripts can be used for most projects:

```text
before_install:
  # Prepares CI environment
  - source ~/.scripts/travis/load-travis-environment.sh
```

This will initialize a set of environment variables to be used by the other scripts.

Some of these will be the following flow control environmental variables:

| Variable | Type |
| :--- | :--- |
| DO\_DEPLOY | boolean |
| DO\_DEPLOY\_RELEASE | boolean |
| DO\_DEPLOY\_DEVELOP | boolean |
| DO\_DEPLOY\_DOCS | boolean |
| DO\_DEPLOY\_DOCS\_RELEASE | boolean |
| DO\_DEPLOY\_DOCS\_DEVELOP | boolean |
| DO\_TEST\_DOCS | boolean |
| DO\_COVERAGE | boolean |

