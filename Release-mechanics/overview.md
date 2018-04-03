# Overview

## gitflow branching model

**Prerequisite reading**: [the original blog post describing gitflow](http://nvie.com/posts/a-successful-git-branching-model/)

Keep a link to the prerequisite reading handy for reference.

## In LDL ...

Because all of our repos follow the gitflow conventions, the dora build/migration/update tool can be simple, almost automatic.

The LDL is composed of all the 'normal' Islandora modules, plus some forks, and some borrowed or adapted from the community, and a few that are original to LSU.

All of the islandora hq modules have release branches, making it easy to update them all by specifying a new version in the build params.

All of the LSU forks and original modules use tags on master for releases and can similarly be updated by specifying a version number, or by just checking out master, provided this gitflow constraint is observed:
>... each time when changes are merged back into master, this is a new production release by definition. We tend to be very strict at this, so that theoretically, we could use a Git hook script to automatically build and roll-out our software to our production servers everytime there was a commit on master.

For the handful of other modules that don't follow a popular scheme, or for which we need to ensure a very specific version, we do so.
