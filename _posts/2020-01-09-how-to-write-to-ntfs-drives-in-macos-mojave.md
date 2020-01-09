---
title: How to Write to NTFS Drives in macOS Mojave
categories: [Mac]
tags: [NTFS, macOS, exFAT]
--- 

In case you use NTFS formatted USB drives on your Mac, you can only open files stored on those drives, but you can’t change those files.

In other words,

* macOS computers mount NTFS formatted USB drives as "Read Only";
* "Read Only" mounted drives cannot be written to with macOS computers.

There are several ways to work around this problem.

## 1. Change Drive Format to exFAT

If you’re going to be transferring files between Mac's and PC's use exFAT. The macOS Mojave supports exFAT file format and since Windows does too, converting an NTFS drive to exFAT may solve the problem of accessing the files it contains on both platforms.

If it’s your case, read this

* [https://support-en.wd.com/app/answers/detail/a_id/20821](https://support-en.wd.com/app/answers/detail/a_id/20821 "How to Format a WD hard drive to exFAT or FAT32 File System").

However you will lose all the data, and in case you forget to backup first, it will be gone forever.

## 2. Apple’s Experimental NTFS-Write Support

The macOS includes experimental support for writing to NTFS drives. However, it’s off by default and requires some messing around in the terminal to enable it.

If you want to take the risk and try them out, read the following tutorial

* [http://osxdaily.com/2013/10/02/enable-ntfs-write-support-mac-os-x/](http://osxdaily.com/2013/10/02/enable-ntfs-write-support-mac-os-x/ "How to Enable NTFS Write Support in Mac OS X").

This solution could potentially cause problems with your NTFS file system, so use it with caution.

## 3. Third Party NTFS Drivers

Last but not least, there are third party paid drivers that allow Mac users to read, write and access NTFS formatted USB drives without reformatting the drive with exFAT or using of experimental features.

* Microsoft NTFS for Mac by Paragon Software
* Microsoft NTFS for Mac by Tuxera
