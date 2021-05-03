---
title: Tuning Ghost and Ubuntu on Raspberry Pi
slug: tuning-ghost-and-ubuntu-on-raspberry-pi
date: 2020-07-13T16:16:48.000Z
date_updated: 2020-07-13T16:28:39.000Z
tags: code

---

SD cards aren't ideal media for hosting a website. However with a few tunes you can extend the life of the SD card and provide a highly performant website to guests.
<!-- excerpt -->

SD cards don't love alot of writes, so to reduce it some I turned off ghosts very promiscuous logging of all traffic to just report on errors only. 

I added `"level": "error",`  to the config file at the root of the the Ghost install at `/var/www/ghost` so the logging entry looks like:

      "logging": {
        "level": "error",
        "transports": [
          "file",
          "stdout"
        ]

I also want to stop the logging of Ubuntu, which logs through the rsyslog daemon. I can stop it with this command: `sudo systemctl stop rsyslog.service` however on restart it will start back up again. To stop logging permentatly you need to use the following command: `sudo systemctl disable rsyslog.service` you can of course trade the disable for enable and start it back up if you need to debug again.

A SD card isn't the most reliable media in general even with logging turned off, so I backup my Ghost install nightly using the excellent Python tool and documentation by [Ganapathy](https://twitter.com/vicke4).
[

How to Setup Automatic Backup for your Ghost Blog

Save yourself from losing your blog data by setting up daily automated backups. Your backups will be saved on Google Drive with 30 revisions.

![](https://www.syncwithtech.org/favicon.ico)Ganapathy SSync With Tech - Tech tips, tutorials, guides

![](https://www.gravatar.com/avatar/cf69d1d53608e86191dac3f7ed66c78b?s=250&amp;d=mm&amp;r=x)
](https://www.syncwithtech.org/automated-backup-ghost-blog/)
Ghost provides alot of other options as well with great  documentation here:
[

Configuration - Adapt your publication to suit your needs

Find out how to configure your Ghost publication or override Ghost’s default behaviour with robust config options, including mail, storage, scheduling and more!

![](https://ghost.org/icons/icon-512x512.png?v=e58c97d95fb227a34fe36491b7d4a4c9)GhostGhost

![](https://ghost.org/images/meta/Ghost-Docs.jpg)
](https://ghost.org/docs/concepts/config/)
