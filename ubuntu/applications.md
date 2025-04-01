---
title: Ubuntu applications
description: 
published: true
date: 2025-04-01T14:06:14.637Z
tags: needs work
editor: markdown
dateCreated: 2025-03-31T16:15:36.104Z
---

# Ubuntu applications

Ubuntu supports a wide range of applications.

* Find a full list of Debian packages on [packages.ubuntu](https://packages.ubuntu.com/)
* Search for available snaps on the [snap store](https://snapcraft.io/store)

Below is a curated list of some popular applications.

## Development

### Environments

The Godot game engine can be downloaded as a snap:

```
sudo snap install godot4
```

### Toolchains

> For detailed information on installing development toolchains on Ubuntu, read the official [Ubuntu for Developers documentation]().
{.is-info}

The Python interpeter is installed by default on Ubuntu and can be used to run scripts right away:

```
python3 myscript.py
```

Toolchains for languages like Go can be installed easily using `apt` or `snap`, for example:

```
sudo snap install go --classic
```

## Media

### Steam

Steam is available as a snap:

```
sudo snap install steam
```

Most games available on Steam should run on Ubuntu.

1. You first need to go to `settings > compatibility`.
2. Click `Enable Steam Play for all other titles`.
3. [optional] Pick a compatibility layer

## Office

LibreOffice is preinstalled when you do a full Ubuntu installation.

It includes tools for preparing documents, slides and spreadsheets.