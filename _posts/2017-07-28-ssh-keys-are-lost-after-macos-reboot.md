---
title: SSH keys are lost after macOS High Sierra reboot
categories: [Mac]
tags: [AWS, macOS, SSH, SSH key]
---

To list all keys run

```bash
ssh-add -l
```

Re-import your SSH key

```bash
ssh-add -K ~/.ssh/id_rsa
```

Add the following to your `~/.ssh/config` file:

```
Host *
   AddKeysToAgent yes
   UseKeychain yes
```

Source: [macOS Sierra doesn’t seem to remember SSH keys between reboots](https://apple.stackexchange.com/questions/254468/macos-sierra-doesn-t-seem-to-remember-ssh-keys-between-reboots)