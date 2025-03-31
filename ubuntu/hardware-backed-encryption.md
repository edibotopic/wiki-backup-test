---
title: How to use hardware backed encryption
description: 
published: true
date: 2025-03-31T15:33:42.038Z
tags: how-to
editor: markdown
dateCreated: 2025-03-31T15:33:02.518Z
---

# How to manage hardware-backed encryption and recovery keys on Ubuntu Desktop


Hardware-backed encryption is a feature that lets you encrypt your computer’s drive with keys that are automatically generated and stored in the computer’s Trusted Platform Module (TPM).

You should always store a recovery key for your encrypted drive somewhere safe to avoid losing access to all your data.

## Check if you need a recovery key

Hardware-backed encryption is a convenient way to keep your data secure. Usually, you only need to enter your Ubuntu user password to get access to your data, unless you decide to set an optional passphrase for additional security.

You may be asked to provide a recovery key on boot if the system detects certain suspicious events, including:

* Changes to hardware components in your computer
* Updates to BIOS, UEFI and firmware
* Changes to boot settings, such as boot order or secure boot
* Errors with authentication, such as entering a wrong password too many times
* Changes to configuration settings, such as organization security policies
* Resetting or clearing of the TPM module

To avoid losing access to your data, get a recovery key and store it somewhere safe.

## Get a recovery key

We strongly recommend that you retrieve a recovery key as soon as possible.

To get a recovery key for your encrypted Ubuntu drive, open a terminal and run this command:

```
sudo snap recovery --show-keys
```

Once retrieved, store it somewhere safe, such as in a password manager. You want the key to be easy to find but also well protected, because anyone with this key could access your personal data.

> We are planning to integrate recovery key creation into the Ubuntu installer and the Security Center. Once this is in place, the above command will no longer be available.
{.is-info}

## Use recovery keys for other operating systems

You should store recovery keys somewhere safe for any other encrypted drives or operating systems that you have installed in your computer. You may need individual recovery keys for each of them in case of the same events outlined above. Updating firmware with the Firmware Updater in Ubuntu may require you to provide recovery keys for other non-Ubuntu drives.

If you use BitLocker on Windows or have an encrypted Windows installation in your machine, check Microsoft’s documentation on how to back up and find recovery keys. If you need to apply changes to your system, you can also disable BitLocker temporarily and re-enable BitLocker after the changes have been made.

When using recovery keys for other platforms, please check the relevant vendor’s documentation.

## What to do if you don’t have a recovery key

If your computer is asking for a recovery key but you don’t have one, try undoing any recent changes to your computer. For example:

* Remove any new hardware components
* Undo any changes to boot settings
* Reboot your computer
* Attempt login again

You can also check if the recovery key was automatically stored in the cloud. Recovery keys for Windows’ BitLocker may be stored on your Microsoft Account or your organization account.