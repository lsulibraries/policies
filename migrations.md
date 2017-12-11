## Migrations

... or _Getting things into production_ ...

### Change classes

Changes to the production system can be classified as follows:

- those that change the architecture of the system at an OS/networking level
- those that change the application configuration in some way
- those that those that change the application code 
- those that change the content of the application

While all four of these classes can be captured in the configuration management activity, the cost/benefit of tracking content changes is too high/low given our current capacity. For the rest of this document, _Change closses_ includes only the first three listed classes.

### Getting into production

Except in certain urgent situations, changes to the Louisiana Digital Library should begin in a development environment, hereafter called [dora box](https://github.com/lsulibraries/dora). This is a vagrant box built to be as close as possible to the production system; see the README for instructions on its use, including how to update module versions, drupal variables, etc.

#### dora development workflow

##### Create a portable environment

Capture your work on a [feature branch](https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow) based on the master branch of the dora box repo. 

Capturing your work in this way makes it possible to share the feature or system configuration that you are interested in. It also enables a final unit test of your work before it goes into the integration test phase, and on to the public environments.

To facilitate these, the branch should include settings for ingesting any relevant collections, setting variables, enabling particular versions of modules, etc. The goal should be that someone else could reprduce your work environment by cloning and vagrant up-ing on your branch.

##### Is it done ?

Once your work is ready to move out of development on its way to production, there needs to be some documentation that describes at the very least 1) the problem or feature this work solves or presents, and 2) steps to test that your work achieves its goal (in the case of a problem or bugfix, including steps to reproduce is highly encouraged).

#### Test and push procedure

Before any work can migrate to production environments, it should be tested as thoroughly as practicable. The level of rigor will vary with the complexity of the work, but in general, you should be able to show that the work 1) accomplishes its goal and 2) that it does not introduce problems in related components.

##### Examples - Drupal/Islandora configuration changes

###### Openseadragon settings

Setting the default zoom level in openseadragon to a new value is a low-complexity, self-contained change, and the testing involved, while important, need not be rigorous.

Scenario: user reports that tall-skinny images are not shown in full 

Assuming you have a dedicated branch all set up, find and ingest a tall-skinny image and verify that the production settings result in the problem condition that the user has reported. If not, first double-check your setup for discrepancy with the production system. If your setup is correct, then seek more information to be gotten from the user.