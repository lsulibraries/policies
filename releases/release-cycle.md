#DRAFT

## In general

These guidelines are written assuming a git-flow development model and adherence to the semantic versioning scheme.

## Release cycle

### Release candidate (RC)

When we are ready to cut a release because:
- known deadline
- enough features accumulated on `develop` branch,
We will create a new branch called x.y.z-rc1, which will pass next to an automated testing phase

### Automated testing

- coding standards checks (when we get fancy)
- Run islandora core tests
- Run lsulibraries (forks, custom modules) tests
- Run behavioral tests (automated browser clicks, selenium)

when these tests are passing, move to a public testing environment (test.louisianadigitallibrary.org).

## Public RC / call for comment

Let RC be deployed in public testing environment for a period of time*.

Once time has elapsed and any discovered problems are addressed, move to production

## Production Release

Cut release branch, repeat....
