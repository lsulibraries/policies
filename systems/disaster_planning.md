## DR plan (from scratch)
This plan assumes:
1. There is a good copy of Fedora object/datastream files
2. There is a blank VM that we can build via ansible
3. There is a Drupal database dump available.


## Plan
1. Create appropriate VM with volumes attached
2. For convenience in this first test, create the fedora volume from last night's snapshot.
3. Run the islandora_ansible build
4. import the mysql db dump
5. stop tomcat and rebuild fedora
6. move Solr index to dedicated volume (see that plan elsewhere ?)
7. Rebuild solr index from foxml files


## Doing it notes
1. Creating the EC2 instance with the correct volumes took a good bit of manual checking, tedious clicking
  - ami is fresh ubuntu 14
  - mounted fedora and solr volumes from snapshot
  - copied fstab from current prod:
          root@ip-172-31-12-252:/mnt# cat /etc/fstab
          LABEL=cloudimg-rootfs   /        ext4   defaults,discard        0 0
          /dev/xvdh /cache ext4 defaults 0 0
          /dev/xvdi /opt/mounts/fedora ext4 defaults 0 0
          /dev/xvdj /opt/mounts/drupal ext4 defaults 0 0
          /dev/xvdk /tmp ext4 defaults 0 0
          /dev/xvdl /mnt/logs ext4 defaults 0 0
          /dev/xvdo /mnt/solr ext4 defaults 0 0

  - create mount points

          mkdir -p /cache /opt/mounts/fedora /opt/mounts/drupal /mnt/logs /mnt/solr

  - make new filesystems on empty volumes:

          mkfs.ext4 /dev/xvdj && mkfs.ext4 /dev/xvdk && mkfs.ext4 /dev/xvdl

  - if you have taken this opportunity to enlarge any of the attached volumes, be sure to resize its filesystem:

          root@ip-172-31-4-104:/home/ubuntu# resize2fs /dev/xvdi
          resize2fs 1.42.9 (4-Feb-2014)
          Filesystem at /dev/xvdi is mounted on /opt/mounts/fedora; on-line resizing required
          old_desc_blocks = 157, new_desc_blocks = 188
          The filesystem on /dev/xvdi is now 786432000 blocks long.


2. Run ansible base (aka islandora_ansible)

  - set group_vars appropriately: (`attach_mounts: false`)

          ---
          environment_type: testing

          ########################
          # mysql
          mysql_root_username: root
          mysql_root_password: root
          mysql_local_installation: true
          mysql_login_host: localhost

          attach_mounts: false
          drupal_reverse_proxies_ips: 172.31.47.14
          fqdn_suffix: drtestlouisianadigitallibrary.org

          php_upload_max_filesize: 12G
          php_post_max_size: 12G
