### Getting into production

Except in certain urgent situations, changes to the Louisiana Digital Library should begin in a development environment, hereafter called [dora box](https://github.com/lsulibraries/dora). This is a vagrant box built to be as close as possible to the production system; see the README for instructions on its use, including how to update module versions, drupal variables, etc.

#### dora development workflow

To begin with (Dec 2017), we are using a pretty loose development workflow consisting of feature. stable, testing and production branches. As we go along, our workflow should become more disciplined in the spirit of a best-practice system like [git flow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow).

##### Create a portable environment

Capture your work on a [feature branch](https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow) based on the master branch of the dora box repo.

Capturing your work in this way makes it possible to share the feature or system configuration that you are interested in. It also enables unit testing of your work (as in _testing the work in isolation as a unit, not function-level unit testing_) before it goes into the integration test phase, and on to the public environments.

To facilitate these, the branch should include everything  needed to reproduce the environment in which this work is relevant: ingesting collections, setting variables, enabling particular versions of modules, etc. The goal should be that someone else could reprduce your work environment by cloning and vagrant up-ing on your branch.

##### Is it done ?

Once your work is ready to move out of development on its way to production, it needs to be tested. You should supply some documentation that describes at the very least 1) the problem or feature this work solves or presents, and 2) steps to test that your work achieves its goal (in the case of a problem or bugfix, including steps to reproduce is highly encouraged). Until there is an obvious best way to do this, include this documentation as a markdown file called testing-<FB-whatever>.md.

#### Test and push procedure

Before any work can migrate to production environments, it should be tested as thoroughly as practicable. The level of rigor will vary with the complexity of the work, but in general, you should be able to show that the work 1) accomplishes its goal and 2) that it does not introduce problems in related components.

##### Examples - Drupal/Islandora configuration changes

###### Openseadragon settings

Setting the default zoom level in openseadragon to a new value is a low-complexity, self-contained change, and the testing involved, while important, need not be rigorous.

Scenario: user reports that tall-skinny images are not shown in full

Assuming you have a dedicated branch all set up, find and ingest a tall-skinny image and verify that the production settings result in the problem condition that the user has reported. If not, first double-check your setup for discrepancy with the production system. If your setup is correct, then seek more information to be gotten from the user.



## gitflow

Currently, we observe the practice of *feature branches*; where each task in a module/theme gets done on a branch checked out from `master`, or whatever the latest official, stable version is called. We do not currently have a mechanism for getting those branches merged back to master in an orderly fashion.
