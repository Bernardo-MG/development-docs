# Continuous integration

After each commit the CI service will take care of validating the changes, building/publishing artifacts and messaging services.

![CI flow][ci_flow]

## Scripts

There is [a repository containing scripts][scripts_repo] developed to help during the CI process. This allows reusing code and instructions, just by copying the repository contents.

[ci_flow]: ../img/diagram/ci_general_activity.png
[scripts_repo]: https://github.com/Bernardo-MG/ci-shell-scripts
