---
title: Create MySQL dump on EC2 instance and download it
categories: [DevOps, Databases]
tags: [SSH, MySQL, EC2, scp, Amazon, mysqldump, macOS, terminal]
---

We're going to create a MySQL dump on an EC2 instance, compress and download this file to our local (Mac) machine.

First of all let's connect to the instance using a `ssh` command:

```bash
ssh -i "/path/to/your/*.pem" <EC2_USERNAME>@<PUBLIC_DNS_NAME>
```

where

* `/path/to/your/*.pem` is the location where the PEM key is stored.
* `EC2_USERNAME` is the username you log in with. If you used Amazon Linux 2 or the Amazon Linux AMI, the user name is ec2-user.
* `PUBLIC_DNS_NAME` is the IP or DNS alias of the instance.

Then use the `mysqldump` utility to export a dump file from the database:

```bash
mysqldump -h <AMAZONAWS_RDS_HOST> -u <USER_NAME> -p <DB_NAME> > <BACKUP_NAME>.sql
```

This file can be compressed

```bash
gzip -f <BACKUP_NAME>.sql
```

**Note!** `-f` option forcefully compresses a file named `<BACKUP_NAME>.sql` even if there already exists a file named as `<BACKUP_NAME>.sql.gz`.

Use `scp` to download the backup file from the EC2 instance to your local machine:

```bash
scp -i "/path/to/your/*.pem" <EC2_USERNAME>@<PUBLIC_DNS_NAME>:/path/to/your/backup ~/Downloads/
```

**Note!** `scp` means "secure copy", which can copy files between computers on a network.

If needed the backup file can be removed on the EC2 instance:

```bash
rm <BACKUP_NAME>.sql.gz
```