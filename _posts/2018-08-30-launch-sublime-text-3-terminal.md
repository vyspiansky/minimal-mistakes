---
title: Launch Sublime Text 3 from the terminal
categories: [Mac]
tags: [command line, terminal, Sublime Text]
---

```
$ echo $PATH
```

Output: /usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin

Create a symbolic link

```
$ ln -s "/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl" /usr/local/bin/subl
```

To open the entire current directory

```
$ subl .
```