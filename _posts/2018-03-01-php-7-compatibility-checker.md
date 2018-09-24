---
title: PHP 7 Compatibility Checker (php7cc)
categories: [PHP]
tags: [PHP 7, Alpine Linux, php7cc]
---

```
$ apk add php7-phar
```

```
$ composer global require sstalle/php7cc
$ php composer.phar global require sstalle/php7cc
$ export PATH="$PATH:$HOME/.composer/vendor/bin"
```

```
$ php7cc /path/to/file.php
```

Source URL: [https://github.com/sstalle/php7cc](https://github.com/sstalle/php7cc)