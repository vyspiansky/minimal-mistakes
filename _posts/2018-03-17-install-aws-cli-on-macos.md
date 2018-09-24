---
title: Install AWS CLI on macOS
categories: [DevOps]
tags: [AWS CLI, Mac, AWS]
---

## Easiest way to install AWS CLI

```
$ brew install awscli
```

See more [http://www.chrisjmendez.com/2017/02/18/aws-installing-aws-client-using-homebrew/](http://www.chrisjmendez.com/2017/02/18/aws-installing-aws-client-using-homebrew/)

## A bit longer way...

```
$ brew install python3
$ python3 --version
```

```
$ sudo mkdir /usr/local/Frameworks
$ sudo chown $(whoami):admin /usr/local/Frameworks
```

```
$ brew link python
```

```
Error: pip3: command not found 
$ brew postinstall python3
$ pip3 --version
```

URL: [https://docs.aws.amazon.com/cli/latest/userguide/cli-install-macos.html](https://docs.aws.amazon.com/cli/latest/userguide/cli-install-macos.html)