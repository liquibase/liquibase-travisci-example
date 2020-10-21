[![Build Status](https://travis-ci.com/liquibase/liquibase-travisci-example.svg?branch=main)](https://travis-ci.com/liquibase/liquibase-travisci-example)

# liquibase-travisci-example
This repo contains an example Travis CI config for running the Liquibase Docker container within your CICD Pipeline.

## .travis.yml
This file is required for Travis CI to run your pipeline.  Our example is broken down into the following:

* language: java - this can be whatever language your app uses

* os: linux

* services: docker - this is required to run the Liquibase Docker container

* env: global: - (optional) these are global environment variables used to define fields required by liquibase in an easier to read format.

* before_install: pulls the version of Liquibase Docker image you'd like to use in your pipeline.

* script: - the docker run command we use to run liquibase against our changeset.

## testing
Make a pull request against this repository with your desired operation, changeLogFile, database username, database password, and database jdbc url.
