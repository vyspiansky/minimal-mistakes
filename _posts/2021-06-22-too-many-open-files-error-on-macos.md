---
title: Too many open files error on macOS
categories: [Mac]
tags: [macOS, ulimit]
---

We're going to increase an `ulimit` setting on macOS, but first let's obtain the current limit of file descriptors via `ulimit -n`.

In case this value has not been changed before, a maximum number of `open files` most likely will be `256`.

To increase this setting execute 

```bash
ulimit -n 12288
```

where `12288` – a desired value.

However keep in mind that `ulimit` changes the limit only for current session. So put this command to your `~/.bash_profile` file:

```bash
echo 'ulimit -n 12288' >> ~/.bash_profile
```