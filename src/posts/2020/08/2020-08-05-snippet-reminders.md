---
title: Snippet Reminders
slug: snippet-reminders
date: 2020-08-05T19:05:13.000Z
date_updated: 2020-10-08T01:36:48.000Z
---

### Get Your Public IP

`curl -s canihazip.com` info about owner [here](https://major.io/icanhazip-com-faq/).

### Let Everyone Execute a Script

`chmod +x script.sh`

### View Permissions on a Script

`ls -l script.sh`

### Edit Cron

`crontab -e`
[

Crontab.guru - The cron schedule expression editor

An easy to use editor for crontab schedules.

The cron schedule expression editor

](https://crontab.guru/every-week)
### Run Code in BASH

    # Run Code
    # If we're on the PiTFT screen (ssh is xterm)
    if [ "$TERM" == "linux" ] ; then
      while :
      do
        sleep 10 # Let everything settle
        ./padd.sh
        sleep 1
      done
    fi

### Setup Wifi

`wpa_supplicant.conf`

    country=us
    update_config=1
    ctrl_interface=/var/run/wpa_supplicant
    
    network={
     scan_ssid=1
     ssid="MyNetworkSSID"
     psk="Pa55w0rd1234"
    }
    

### Find a File

`find / -iname "filename"`

### Copy a Remote File to a Local System using the `scp` Command

    scp remote_username@10.10.0.2:/remote/file.txt /local/directory

Add `-r` to make it recursive to the folder.

## All the Various Date Formats

[Link](https://tecadmin.net/get-current-date-time-python/)

## Passwordless SSH
[

Passwordless SSH access - Raspberry Pi Documentation

Need to access a Raspberry Pi, but don’t have a monitor spare? This section provides basic instructions for setting up remote access.

![](https://www.raspberrypi.org/app/themes/mind-control/images/favicon.png)Raspberry Pi Documentation

![](https://www.raspberrypi.org/app/themes/mind-control/images/octocat.jpg)
](https://www.raspberrypi.org/documentation/remote-access/ssh/passwordless.md)
## Rmate to edit Raspberry Pi
[

Editing Raspberry Pi Code Remotely from Visual Studio Code

Use Visual Studio Code across your network to edit files on your Raspberry Pi. By Ladvien.

![](https://prod.hackster-cdn.online/assets/favicons/apple-touch-icon-180x180-e4919391d8a5a61764099e7f7d06641e43f6964e591f155752d5be470aabaaa9.png?v=zXX3Bm3lo3)LadvienHackster.io

![](https://hackster.imgix.net/uploads/attachments/495333/nano_vs_vsc.png?auto=compress%2Cformat&amp;w=600&amp;h=450&amp;fit=min)
](https://www.hackster.io/Ladvien/editing-raspberry-pi-code-remotely-from-visual-studio-code-9d42e0)
> [Visual Studio Code remote file editing on Raspberry Pi](https://rohn.io/visual-studio-code-remote-file-editing-on-raspberry-pi)

<!--//--><![CDATA[//><!--
		/*! This file is auto-generated */
		!function(d,l){"use strict";var e=!1,o=!1;if(l.querySelector)if(d.addEventListener)e=!0;if(d.wp=d.wp||{},!d.wp.receiveEmbedMessage)if(d.wp.receiveEmbedMessage=function(e){var t=e.data;if(t)if(t.secret||t.message||t.value)if(!/[^a-zA-Z0-9]/.test(t.secret)){var r,a,i,s,n,o=l.querySelectorAll('iframe[data-secret="'+t.secret+'"]'),c=l.querySelectorAll('blockquote[data-secret="'+t.secret+'"]');for(r=0;r<c.length;r++)c[r].style.display="none";for(r=0;r<o.length;r++)if(a=o[r],e.source===a.contentWindow){if(a.removeAttribute("style"),"height"===t.message){if(1e3<(i=parseInt(t.value,10)))i=1e3;else if(~~i<200)i=200;a.height=i}if("link"===t.message)if(s=l.createElement("a"),n=l.createElement("a"),s.href=a.getAttribute("src"),n.href=t.value,n.host===s.host)if(l.activeElement===a)d.top.location.href=t.value}}},e)d.addEventListener("message",d.wp.receiveEmbedMessage,!1),l.addEventListener("DOMContentLoaded",t,!1),d.addEventListener("load",t,!1);function t(){if(!o){o=!0;var e,t,r,a,i=-1!==navigator.appVersion.indexOf("MSIE 10"),s=!!navigator.userAgent.match(/Trident.*rv:11\./),n=l.querySelectorAll("iframe.wp-embedded-content");for(t=0;t<n.length;t++){if(!(r=n[t]).getAttribute("data-secret"))a=Math.random().toString(36).substr(2,10),r.src+="#?secret="+a,r.setAttribute("data-secret",a);if(i||s)(e=r.cloneNode(!0)).removeAttribute("security"),r.parentNode.replaceChild(e,r)}}}}(window,document);
//--><!]]>

but use `sudo pip install rmate`

## How to test the write speed of SD cards

`sudo ./sd_card_speed_test.sh /Volumes/Untitled`
[

biodranik/sd-card-speed-test

Bash script for Mac OS X and Linux to test SD card or SSD/HDD read and write speed. - biodranik/sd-card-speed-test

![](https://github.githubassets.com/favicons/favicon.svg)biodranikGitHub

![](https://avatars1.githubusercontent.com/u/170263?s=400&amp;v=4)
](https://github.com/biodranik/sd-card-speed-test)
