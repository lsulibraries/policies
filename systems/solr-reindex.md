## Speed

Speed is terrible using the following:
~~~
#### 5. Rebuild solr index
cd /usr/local/tomcat/webapps/fedoragsearch/client/
sh runRESTClient.sh  http://localhost:8080/fedoragsearch/rest updateIndex fromFoxmlFiles
~~~

Reported by others here: https://groups.google.com/forum/#!topic/islandora/BKcuX-z7LFc

From 16:30 yesterday until 13:57 today, 2018-04-12, solr only reports ~13,000 items in its index.

## Scripted

- get a list of pids

~~~
SELECT pid FROM doFields \
INTO OUTFILE '/tmp/pids.csv' \
FIELDS TERMINATED BY ',' \
FIELDS ESCAPED BY '\' \
LINES TERMINATED BY '\n';
~~~

- feed the list to a script that posts to gsearch

### Nick's
https://gist.github.com/ruebot/82872fb8861c82f81416

- 490 items indexed in one minute !


### Jason's
https://github.com/lsulibraries/islandora_utils/blob/e98274142308ae304cc8008b222d8bde21af38e6/islandora_utils.drush.inc#L49

- 531 per minute with outfile...

- started at just after 14:00 2018-04-12
- but starts to hit the gsearch timeout sometime during the night; killed this am at 0924 with 90757 items in the solr index.
