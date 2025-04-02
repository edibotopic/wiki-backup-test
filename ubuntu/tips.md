---
title: Tips
description: Quick tips for getting the best out of Ubuntu
published: true
date: 2025-04-02T15:59:36.814Z
tags: needs work
editor: markdown
dateCreated: 2025-03-04T12:25:04.784Z
---

# Trying Ubuntu on Windows

## WSL

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

## Dual boot

You can also run a full Ubuntu installation side-by-side with Windows.

This is known as "dual booting" and provides a more complete Ubuntu experience.

Dual booting can require significant amounts of storage.

> Read the wiki page on [how to dual-boot Ubuntu with Windows](/ubuntu/dual-boot)
{.is-info}

# Terminal

## Commands

> How do I confirm what Ubuntu version I am using?

```bash
lsb_release -a
```

> How do I update available packages from the terminal?

```bash
sudo apt update
```

## Foot terminal not running

> The Foot terminal is installed on Ubuntu but it won't run?

Foot, like some other applications, only runs on Wayland.

By default, Ubuntu uses the Wayland display server.
If a GPU with limited Wayland compatibility is detected, Ubuntu uses X11.

If you try to run Foot on X11, it will not display.
You can check which display server you are using in the login screen.