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

# How To Run the Example

1. Fork and clone the liquibase-travisci-example repository.
> Fork by clicking the "Fork" button at the top right of the liquibase-travisci-example page.

> git clone git@github.com:<YOURFORK>/liquibase/liquibase-travisci-example.git
2. Create a new git branch for your changes.
> git checkout -b <your_branch_name>
3. Edit example/changelogs/samplechangelog.h2.sql to add a new changeset. Replace "yourname" with a unique identifier.
```
--changeset yourname:yourname1
--rollback DROP TABLE yourname;
CREATE TABLE yourname (
    id int primary key,
    name varchar(50) not null,
)
```

4. Add, commit and push your changes to GitHub.
> git add example/changelogs/samplechangelog.h2.sql
> git commit -m "yourname: Adding new changeset for example"
> git push origin <your_branch_name>
5. Your commit triggers a build in TravisCI and executes Liquibase update!

If you want to try with your own changelog and database, you can make a pull request against this repository with your desired operation, changeLogFile, database username, database password, and database jdbc url.

 
 # Troubleshooting
 * If your build fails due to a validation error, verify that your changeset author and ID are unique in the changelog. This is the `changeset yourname:yourname1`, where the left side is your author and the right is the changeset ID.
 * If Liquibase Update fails, verify that your table name is unique in the changelog.

# Get More Liquibase!
Get documentation at https://docs.liquibase.com      
Get certified courses at https://learn.liquibase.com  
Get support at https://liquibase.com/support         


Copyright 2020 Datical, Inc. All rights reserved. The program is subject to the 
license agreement, copyright, trademark, patent, and other laws.
