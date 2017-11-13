## Migrations

... or _Getting things into production_ ...

### Change classes

Changes to the production system can be classified as follows:

- those that change the architecture of the system at an OS/networking level
- those that change the application configuration in some way
- those that those that change the application code 
- those that change the content of the application

While all four of these classes can be captured in the configuration management activity, the cost/benefit of tracking content changes is too high/low given our current capacity. For the rest of this document, _Change closses_ includes only the first three listed classes.

### LDL

Except in certain situations, changes to the Louisiana Digital Library begin in a development environment, hereafter called [dora box](https://github.com/lsulibraries/dora). This is a vagrant box built to be as close as possible to the production system; see the README for instructions on its use, including how to update module versions, drupal variables, etc.

Once a change is made and tested in the dev environment, capture it in a [feature branch](https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow) on the dora box repo. At this point, pushing your feature branch to github implies that the change is ready for review prior to integration with the production environment.

... wip...