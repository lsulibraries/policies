
# Infrastructure

Islandora refers to a suite of open source applications. Digital objects and metadata are stored in an instance of [Fedora Commons digital repository system](http://www.fedora-commons.org/). The front end display is provided by [Drupal](https://www.drupal.org/), a content management system used for many websites, including [LSU Libraries' website](http://lib.lsu.edu/). Search is handled by [Apache Solr](https://lucene.apache.org/solr/). 

More information about the software framework of Islandora is provided in the [Islandora documentation](https://wiki.duraspace.org/display/ISLANDORA/About+Islandora). Additionally, the Florida Virtual Campus maintains excellent documentation as a publicly available wiki at [FL-Islandora Guides](https://fig.wiki.flvc.org/wiki/index.php/Main_Page).

# Cloud hosting

The LDL is hosted on Amazon Web Services (AWS), an industry standard web services platform. This provides the LDL with a responsive, reliable, secure, and scalable environment that is also cost-effective. Due to the distributed nature of the AWS cloud, multiple copies of any application or object exist.

# Backups
Backups are automated through AWS. Database, application, and application data (Fedora objects) are backed up nightly. Database backups are taken and managed by Amazon RDS. On the application server, each data volume is snapshotted each night, invoked in a cron-like way from Amazon CloudWatch.

Additional local backups are captured and maintained by the LDL development team.

# Namespace and PID

Items in the LDL have a persistent and unique URLs composed of three main parts. 

* Institution code. This is a unique collection of letters that identifies an institution. 
* Colleciton code. This is a unique collection of letters and/or numbers that identify a collection. For collections migrated from the earlier CONTENTdm version of the LDL, these codes were retained. 
* PID. This is an auto-generated unique number that the software uses to differentiate items. 

URLs are constructed in the following fasion: 

http://louisianadigitallibrary.org/islandora/object/[institution code]-[collection code]:[PID]

An example:

http://louisianadigitallibrary.org/islandora/object/lsu-p15140coll12:192

* institution code = lsu
* collection code = p15140coll12
* PID = 192

_Note: Often in URLs, colons_ (:) _encode as_ %3A _so you will likely see the URLs with the following form: http://louisianadigitallibrary.org/islandora/object/lsu-p15140coll12%3A192.

# Collection landing pages
Although it's not necessarily an "out-of-the-box" feature of Islandora, the LDL Development Team sought to maintain the collection landing pages that are used in the CONTENTdm version of the LDL. These landing pages often include a description of the collection, sometimes with additional content and/or context. Many of the landing pages include a banner image as well. From the landing page are links to the collection objects.

# Test instances
In addition to the production instance of the LDL at http://louisianadigitallibrary.org, there is a test instance of the LDL at http://test.louisianadigitallibrary.org. The test instance can be used to test out new features, new collections, or as a training instance.

Additionally, local instances of the LDL can be installed using Vagrant and VirtualBox (open source virtualization software). The LDL Development Team uses these local instances to experiment with configuration and customization. For additional information about this option, please contact diglib@lsu.ed.

