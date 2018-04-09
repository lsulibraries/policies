*LDL release*

I'm pleased to announce that we are putting the finishing touches on the LDL 0.9.0 release.

The [testing instance](http://test.louisianadigitallibrary.org/) has been updated with this release; please check it out, report any problems, and enjoy the excellent new mobile theme for compounds.

---

There is now a [changelog file](https://github.com/lsulibraries/dora/blob/release-0.9.0/CHANGELOG.md) in the top-level of the dora repo that will be used to capture
change summaries for each release. There is also the beginnings of a [manual] [test plan](https://github.com/lsulibraries/dora/blob/release-0.9.0/testing.md) that will be used to test each release.

Please feel welcomed to add or edit items in the Changelog and test plan*.

---

Unless there are strong arguments against it, I propose that we mint version 1.0.0 once we have satisfied our LDL 'delivery requirements', based on [LDL_delivery.md](https://github.com/lsulibraries/policies/blob/master/LDL_delivery.md) which has been revised recently in group discussion.

---

* If anyone has written already, or knows of a document that captures our bespoke features, I would like to work it into this test plan. The test plan should grow quickly and evolve towards automation in the short term. Many/most islandora modules provide some level of automated tests, and we should look forward to writing tests for our forks and custom modules. Also, behavioral testing, such as that using a scripted browser (via selenium) to click through various user routines can significantly increase team confidence; we should strive to establish it in our release cycle asap.
