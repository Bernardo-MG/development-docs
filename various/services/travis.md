# Travis

Recommended free [CI service](https://travis-ci.org/).

Their [docs](https://docs.travis-ci.com/) are helpful and cover most use cases and problems.

## Configuration

The CI process is prepared with the help of a YAML file, the .travis.yml. All projects include one of these.

As commented before, all the information is included in their docs.

### Environmental variables

Remember that Travis gives support to environmental variables, which can be configured for each project. This is preffered to using encrypred variables in the YAML file.

## Integration

Travis integrates well with other services such as Github or Bintray.

## Complex flows

By default Travis only gives support to simple CI flows. It is recommended using shell scripts to cover this limitation.

There is a set of [CI scripts](https://github.com/Bernardo-MG/ci-shell-scripts) which can help with this.

