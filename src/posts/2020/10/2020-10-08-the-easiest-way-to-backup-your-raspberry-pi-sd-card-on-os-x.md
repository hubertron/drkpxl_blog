---
title: The Easiest Way to Backup your Raspberry Pi SD card on OS X
slug: the-easiest-way-to-backup-your-raspberry-pi-sd-card-on-os-x
date: 2020-10-08T16:27:24.000Z
date_updated: 2020-10-08T16:27:24.000Z
tags: code, raspberrypi
---

The absolute easiest to remember way to back up your Raspberry Pi SD card on a Mac running a modern version of OS X.
<!-- excerpt -->

To back up your Raspberry Pi SD  card follow these simple steps.

## Command Line Approach

**Step 1: **Run `diskutil list` from the command line
**Step 2: **Determine the SD card of the Pi, and unmount it with `diskutil unmount /dev/disk2s1`
**Step 3: **Save the file to your hard drive with the following command: `sudo dd bs=16m if=/dev/rdisk2 of=backup.img`

and to restore: `sudo dd bs=16m if=backup.img of=/dev/disk2`

If you are impatient you can hit `CTRL + T` to get status of the transfer

## GUI Approach

There are many ways to back back up your Pi's SD card, but I have found this one the easiest to remember how to do only doing it once or twice a year since it uses Disk Utility.

If you haven't given Disk Utility "Full Disk Access" You will need to do these steps only once.

**Step 1:** In your Preferences go to > Security and Privacy > Privacy
**Step 2: **Hit lock button and enter password
**Step 3: **Hit the `+` button, search `disk utility` and add, save and close out
![](/assets/img/posts/2020/10/Screen-Shot-2020-10-07-at-5.02.15-PM-1.png)
Once that is done backing up is easy and can be done with only a few clicks.

**Step 1: **Open Disk Utility, hit **`⌘2`**so all disks are shown
**Step 2: **Right click on the top level volume of the SD card you want to back up and select `Image From ...`. It's "Centon DS" in my example below 
![](/assets/img/posts/2020/10/Screen-Shot-2020-10-07-at-5.07.28-PM.png)
**Step 3: **Name the file what you want but before you save change the format from `read-only` to `compressed` or `read/write` depending on your needs.
![](/assets/img/posts/2020/10/Screen-Shot-2020-10-07-at-6.57.38-PM.png)
That's it folks! 3 very quick steps to backing up your Raspberry Pi SD card on a Mac! With the ISO file you can easily use Etcher to deploy the image on other Pi's or replace a worn out SD card.

I hope you find this helpful!
