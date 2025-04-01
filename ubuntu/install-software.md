---
title: How to install software
description: Software on Ubuntu
published: true
date: 2025-04-01T08:00:14.114Z
tags: how-to
editor: markdown
dateCreated: 2025-03-04T12:17:19.372Z
---

# Software

Ubuntu on Desktop is designed to work out-of-the-box and comes pre-packaged with tools suitable for all users.

## Installing software

To install additional packages you have a variety of options.

### App center

The app center is a graphical tool for installing software on Ubuntu Desktop. 

Press <kbd>super</kbd> and start typing `app center` to find it.

### Debian packages

Ubuntu is downstream of Debian and maintains up-to-date archives of `.deb` packages.
They can be installed with.

```bash
sudo apt install <package>
```

### Snap

Ubuntu supports snaps, a containerised and secure format for software packages that can be installed like this:

```bash
sudo snap install <package>
```
