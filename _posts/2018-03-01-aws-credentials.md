---
title: Working with AWS credentials on macOS
categories: [DevOps]
tags: [AWS, macOS]
---

## Check credentials

```
$ aws configure list
```

## Add credentials

```
$ nano ~/.aws/credentials
```

```
[default]
aws_access_key_id=<…>
aws_secret_access_key=<…>
```