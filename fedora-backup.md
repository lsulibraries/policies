Backup fedora data periodically.

## Description
A Fedora repository, and the content of the LDL therefore, can be [rebuilt following a system failure](https://wiki.duraspace.org/pages/viewpage.action?pageId=66585946), provided there is a reliable copy of its data available. In order to reduce the possibility of data loss in the Louisiana Digital Library, ensure that this file system is backed up.

## Strategy
Every night, update backups in AWS' S3 and in Libraries' local infrastructure.

__ToDo__ find at least one partner institution to add as a nightly synced node, á la [LOCKSS](https://www.lockss.org/). A partner should be geographically and geopolitically distant/different.

### Efficacy
Amazon's S3 provides data protection/durability beyond what LSU (or almost anyone) can offer (see ["Data Protection"](https://aws.amazon.com/s3/faqs/)),
however, S3 has gone down before, albeit temporarily:
- https://aws.amazon.com/message/41926/,
- https://www.theverge.com/2017/3/2/14792442/amazon-s3-outage-cause-typo-internet-server

The local backup protects this data against something going terribly wrong at Amazon someday.
Swapping backups with another institution guards against the scenario where both S3 and our local backup is lost.

## Access
S3 bucket [ldl-fedora-data](https://s3.console.aws.amazon.com/s3/buckets/ldl-fedora-data/?region=us-west-2&tab=overview) is only accessible to AWS account holders that are also members of the *[group-to-be-created]* group in the lsulibraries account. Check out the policy describing membership in that group here [Link to as yet unwritten policy](), and the policy describing [lsulibraries AWS accounts]().

The local backup is just a large USB drive attached to the workstation in MIDDL 5A6; uses [EXT4 file system](https://en.wikipedia.org/wiki/Ext4).

Access our partner institution backup by ...

## Implementation Details
Incrementally copy files from the production repository to S3 bucket and to local storage.

The S3 transfer is made using the [official](https://docs.aws.amazon.com/cli/latest/userguide/installing.html) AWS [command-line tools](https://github.com/aws/aws-cli), transfer to local storage uses [rsync](https://en.wikipedia.org/wiki/Rsync).

The use of two different tools is intentional - it helps guard against the possibility of a flaw in either one affecting the integrity of both backups.

### Server-side
Sync the files to S3 bucket *ldl-fedora-data* using aws cli.
In crontab (`crontab -e`):

`52 1 * * * /usr/local/bin/aws s3 sync /usr/local/fedora/ s3://ldl-fedora-data/`

The awscli needs to [run as](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html) an AWS [IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html) user with the following policy attached:

~~~

{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": "s3:ListBucket",
            "Resource": "arn:aws:s3:::ldl-fedora-data"
        },
        {
            "Sid": "VisualEditor1",
            "Effect": "Allow",
            "Action": [
                "s3:PutObject",
                "s3:GetObject",
                "s3:DeleteObject"
            ],
            "Resource": "arn:aws:s3:::ldl-fedora-data/*"
        }
    ]
}

~~~

### Local backup
Sync nightly (preferably after the S3 sync) via rsync to local storage
In crontab (`crontab -e`):

`42 05 * * * rsync -avz --delete -e "ssh -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null" --progress user@box:/usr/local/fedora/data/ /path/to/ldl-fedora-data/ --include="objectStore/***" --include="datastreamStore/***" --exclude="*"`


## Further questions

- Confidence monitoring: how to know the nightly sync happened ?
  - check file modification times,
  - write to a log file in the OS
  - [S3 logging](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/logging-management-and-data-events-with-cloudtrail.html?icmpid=docs_cloudtrail_console#logging-data-events)
- Data integrity: how to ensure that the backup is consistent with prod data (at the time of creation/sync) ?
  - checksum at sync begin, compare to checksum of backups after sync
- What is the requirement for snapshots in time ? that is, if we discover corruption in the backup, it would be useful to revert to a previous point in time.
  - EC2 [volume snapshots](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSSnapshots.html) (currently taken nightly, deleted manually periodically)
  - S3 [object versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/ObjectVersioning.html)
  - some local versioning solution

## Resources

- AWS S3 cron [example](https://faish.al/2015/11/29/aws-s3-sync-using-crontab/)
- rsync [cheat sheet](https://www.digitalocean.com/community/tutorials/how-to-copy-files-with-rsync-over-ssh)
