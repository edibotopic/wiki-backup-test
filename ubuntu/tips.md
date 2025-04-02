---
title: Tips
description: Quick tips for getting the best out of Ubuntu
published: true
date: 2025-04-02T15:20:33.008Z
tags: needs work
editor: markdown
dateCreated: 2025-03-04T12:25:04.784Z
---

# Trying Ubuntu

> What's the easiest way to try Ubuntu as a Windows user?

You can get the full terminal experience using WSL.
Ubuntu is the default Linux distro on WSL.

Installation on Windows 11 is as easy as:

```
wsl --install
```

This will install Ubuntu and place you in an Ubuntu terminal session.
You can also launch graphical applications from the terminal:

```bash
sudo apt install nautilus # install the Ubuntu graphical file manager
nautilus # run the graphical file manager
```

# Terminal commands

> How do I confirm what Ubuntu version I am using?

```bash
lsb_release -a
```

> How do I update available packages from the terminal?

```bash
sudo apt update
```

> How do I open the current directory in the file explorer from the terminal?

```bash
nautilus .
```
