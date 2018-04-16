# fedora DR routine

## Prerequisites:

- fedora should be installed
  - XACML should be there
  -

~~~
#!/bin/bash
####
#### start rebuild setup here
####
####
#### 1a. Shutdown fedora in order to remove everything.
service tomcat7 stop
cd /usr/local/fedora/data/

####
####
#### 1b. For a simulation, create a backup
rsync -avz objectStore datastreamStore /path/to/backup/location/

#### 1c. Remove solr index, for a simulation.
rm -rf /usr/local/solr/collection1/data/index/* /usr/local/solr/collection1/data/tlog/*

#### 2. In all cases, move your backup into place:
rsync -avz /path/to/backup/location/* /usr/local/fedora/data/
chown -R tomcat7.tomcat7 /usr/local/fedora/data/

#### 3. Begin the rebuild.
export CATALINA_HOME=/usr/local/tomcat
#### Rebuild resource index
#### But first, become fedora user. # https://github.com/discoverygarden/trippi-sail/wiki/Replacing-Mulgara-with-Blazegraph#on-fedora-server
su - fedora -s /bin/bash   
sh /usr/local/fedora/server/bin/fedora-rebuild.sh ## choosing option 1
#### time passes...
#### Rebuild SQL
sh /usr/local/fedora/server/bin/fedora-rebuild.sh ## choosing option 2

#### 4. Restart fedora
chown -R tomcat7.tomcat7 /usr/local/fedora/data/
service tomcat7 start
less /usr/local/fedora/server/logs/fedora.log

#### 5a. Update solr config as appropriate.

#### 5. Rebuild solr index
cd /usr/local/tomcat/webapps/fedoragsearch/client/
sh runRESTClient.sh
sh runRESTClient.sh  http://localhost:8080/fedoragsearch/rest updateIndex fromFoxmlFiles

~~~

## Notes
- may have had to ensure content models were installed at islandora/soln-packs/required-objects...
- namespace restrictions were set to 'islandora'; had to remove...
  - 'Limit results to specific namespaces' at /admin/islandora/search/islandora_solr/settings
  - 'Enforce namespace restrictions' at /admin/islandora/configure
- prob need to disable islandora_social_metatags (or possibly configure it) to avoid 60 second page load DELAY

- need fstab

~~~
root@ip-172-31-4-216:/home/ubuntu# cat /etc/fstab
LABEL=cloudimg-rootfs   /        ext4   defaults,discard        0 0
/dev/xvdh /cache ext4 defaults 0 0
/dev/xvdi /opt/mounts/fedora ext4 defaults 0 0
/dev/xvdj /opt/mounts/drupal ext4 defaults 0 0
#/dev/xvdk /tmp ext4 defaults 0 0
/dev/xvdl /mnt/logs ext4 defaults 0 0
/dev/xvdr /mnt/solr ext4 defaults 0 0
#/dev/xvdp none      swap sw       0 0
~~~


## Lingering differences
Between the existing production system and one built from fedora backup:

- users
- institution meta
-
