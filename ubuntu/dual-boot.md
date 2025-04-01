---
title: How to dual-boot Ubuntu
description: Use Ubuntu side-by-side with your current OS
published: true
date: 2025-04-01T15:45:41.337Z
tags: how-to, needs work, out of date
editor: markdown
dateCreated: 2025-04-01T08:25:15.664Z
---

# How to dual-boot Ubuntu with Windows

> This content is borrowed from the Community Help Wiki
{.is-info}

# Introduction

This page describes how to set up your computer in order to dual boot Ubuntu and Windows. Warning /!\ While there are some benefits to dual-booting (e.g. better performance for a native install), it is not recommended. Instead, it is best to do a native install of Ubuntu, and then virtualize the other operating system.

# Back Up Your Data

Although this may seem obvious, it is important to back up your files to an external backup medium before attempting a dual-boot installation (or any other hard drive manipulation), in case your hard drive becomes corrupted during the process. External hard drives, USB flash drives, and multiple DVDs or CDs are all useful for this purpose.

# Have a Windows recovery CD/DVD available

Some computer manufacturers that pre-install Windows provide a Windows recovery/re-installation CD or DVD with the computer. However, many companies no longer ship a physical disc but instead create a hidden partition on the hard drive in which the recovery-disk information is stored. A utility is then usually provided which allows the user to burn a recovery/re-installation CD or DVD from it. If you are buying a new computer and intend on dual-booting, make sure you have (or can make) a physical Windows recovery/re-installation CD or DVD. If neither a CD/DVD nor a recovery partition/burning utility is provided by your computer manufacturer, you may need to contact your vendor and ask for a CD or DVD (to which you are normally entitled under the Windows EULA).

# Getting Recovery Media

You may need to request a physical recovery/re-installation CD or DVD directly from your computer manufacturer. See WindowsRecoveryCd.

Once you have created a physical backup disc from a restore-image partition on the hard-drive, the restore-image partition can either be removed or left in place. Ubuntu can be installed with it intact without problems.

# Install Ubuntu after Windows

A Windows OS should be installed first, because its bootloader is very particular and the installer tends to overwrite the entire hard drive, wiping out any data stored on it. If Windows isn't already installed, install it first. If you are able to partition the drive prior to installing Windows, leave space for Ubuntu during the initial partitioning process. Then you won't have to resize your NTFS partition to make room for Ubuntu later, saving a bit of time.

When a Windows installation already occupies the entire hard drive, its partition needs to be shrunk, creating free space for the Ubuntu partition. You can do this during the Ubuntu installation procedure, or you can see How to Resize Windows Partitions for other options.

If you have resized a Windows 7 or Vista partition and cannot boot up Windows, you can use the instructions from WindowsRecovery to fix it.

# Install Ubuntu

1. Download an Ubuntu LiveCD image (.iso) from Ubuntu Downloads and burn it to a disc (see BurningIsoHowto).
2. Insert the LiveCD into your CD-ROM drive and reboot your PC.
3. If the computer does not boot from the CD (e.g. Windows starts again instead), reboot and check your BIOS settings by pressing F2, F12, Delete, or ESC. Select "boot from CD".
4. Proceed with installation until you are asked this question: "How do you want to partition the disk?".
5. If you have already partitioned the disk and left space for Ubuntu, install it to that and then follow the rest of the steps.
6. Otherwise, choose one of the next two steps. 

# Automatic partition resizing (not recommended)

1. Choose the first option, which should say "Install them side by side, choosing between them each startup".
2. Specify the size of the new partition by dragging the slider at the bottom of the window.
3. Click on "Forward".

Continue on to Finishing Ubuntu Installation 

# Manual partitioning

1. Choose "Manually edit partition table".
2. Listed will be your current partitions.
3. Select the partition you want to resize and press Enter.
4. Select "Size:", press Enter.
5. Select Yes, press Enter.
6. Type in a new size in gigabytes for your partition, it's recommended you free up at least 10 GB of free space for your Ubuntu install. Press Enter when happy with your changes. It may take some time to apply the changes.
7. Create a swap partition of at least your amount of RAM (if you don't know, 8000 MB is a good value).
8. Create a partition for your Ubuntu installation.
9. Create other partitions if necessary: see DiskSpace
10. Select "Finish partitioning and write changes to disk". 

# Master Boot Record and Boot Manager

GRUB2 is the boot manager installed in Ubuntu by default. GRUB2 is an open source boot manager that install the main parts of the boot loaders inside Ubuntu. This means Ubuntu is independent and avoids any need for writing to other operating systems. To accomplish this, the only thing in your computer outside of Ubuntu that needs to be changed is a small code in the MBR (Master Boot Record) of the first hard disk, or the EFI partition. The boot code is changed to point to the boot loader in Ubuntu. You will be presented with a list of operating systems and you can choose one to boot. If you do nothing the first option will boot after a ten second countdown. If you select Windows then GRUB or LILO will chain-load Windows for you at the Windows boot sector, which is the first sector of the Windows partition.

Windows Vista no longer utilizes boot.ini, ntdetect.com, and ntldr when booting. Instead, Vista stores all data for its new boot manager in a boot folder. Windows Vista ships with an command line utility called bcdedit.exe, which requires administrator credentials to use. You may want to read http://go.microsoft.com/fwlink/?LinkId=112156 about it.

Using a command line utility always has its learning curve, so a more productive and better job can be done with a free utility called EasyBCD, developed and mastered during the times of Vista Beta. EasyBCD is very user friendly and many Vista users highly recommend it.

# Installing Windows After Ubuntu

There are two different approaches:

## 1. Recovering GRUB after reinstalling Windows

Please refer to the Reinstalling GRUB2 guide.

## 2. Master Boot Record backup and replacement

This method does not work for computers with UEFI boot. In consequence, it won't work for pre-installed Windows 8 and some pre-installed with Windows 7.

Back-up the existing MBR, install Windows, replace your backup overwriting the Windows boot code:

1. Create an NTFS partition for Windows (using fdisk, GParted or whatever tool you are familiar with)
2. Backup the MBR e.g. dd if=/dev/sda of=/mbr.bin bs=446 count=1
3. Install Windows
4. Boot into a LiveCD
5. Mount your root partition in the LiveCD
6. Restore the MBR e.g. dd if=/media/sda/mbr.bin of=/dev/sda bs=446 count=1
7. Restart and Ubuntu will boot
8. Setup GRUB to boot Windows 