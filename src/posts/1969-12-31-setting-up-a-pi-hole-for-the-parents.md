---
title: Setting up a Pi-Hole for the Parents
slug: setting-up-a-pi-hole-for-the-parents
date_published: 1970-01-01T00:00:00.000Z
date_updated: 2020-09-15T15:53:56.000Z
draft: true
---

This year I got the crazy idea in my head of setting up a Pi-Hole for my parents across the country. I new I would be driving over to them (since this whole COVID thing) so I could take a bunch of random stuff with me like an extra keyboard :)

Having set up Pi-Hole a few times in the past I knew it was pretty easy but I was concernd about maintaining it remotely. They have an ISP that drops out alot so I couldn't rely on remoting in to it directly and I didn't want to deal with the security hastle of having to poke holes through their router so the plan I came up with is as follows:

1. Install Pi-Hole and Configure Pi-Hole
2. Add Block Lists
3. Install a reverse tunnel with NGROK
4. Set up services/cron to auto start tunnel, update Pi-Hole, reboot the box
5. Add in Speedtest to specfic servers so I can see if its a network issue when our Facetime's fails
6. Create a visual display for them to know its working
7. Backing it all up

While the above steps took me some time to figure out this tutorial should take no longer than 30 minutes provides you have an update to date version of Raspian running on your Pi. 

## Part 1: Setting Up Raspberry Pi

## Part 2: Installing and Configuring Pi-Hole

## Part 3: Adding Block Lists

## Part 4: Installing and Configuring a reverse tunnel

## Part 5: Setting Up Automation

## Part 6: Fetching Photos from Google

    pipenv run gphotos-sync /home/pi/gphotos-sync --album "FamilyShare" --flush-index --skip-video  --max-retries 10 --omit-album-date --use-hardlinks

## Part 7: Displaying Photos

Edit autostart: `sudo nano /etc/xdg/lxsession/LXDE-pi/autostart`

    @lxpanel --profile LXDE-pi
    @pcmanfm --desktop --profile LXDE-pi
    @xscreensaver -no-splash
    @/usr/bin/python3 /home/pi/pi3d_demos/PictureFrame2020.py -p /home/pi/gphotos-sync/albums/ -v 60 -s 0 -n 50 --blur_edges True --blur_amount 9 --blur_zoom 1.5 --edge_alpha .9 --fps 24

## Part 8: Backing up the Pi in case I need to ship them a new SD card

## Part 8: Building a Case
[

ngrok - secure introspectable tunnels to localhost

ngrok secure introspectable tunnels to localhost webhook development tool and debugging tool

![](https://dashboard.ngrok.com/static/favicon.ico)inconshreveablesecure introspectable tunnels to localhost

](https://dashboard.ngrok.com/status/tunnels)[

PiTunnel - Access your Raspberry Pi projects from anywhere

![](https://www.pitunnel.com/apple-touch-icon.png)PiTunnel

![](https://www.pitunnel.com/static/images/logo-dark.png)
](https://www.pitunnel.com/devices)[

start request repeated too quickly

I’m writing a bash-script but I often face this issue.
When I try to start or stop a service I often get: start request repeated too quickly How can I solve this problem?
It’s for example when I...

![](https://cdn.sstatic.net/Sites/stackoverflow/Img/apple-touch-icon.png?v=c78bd457575a)lovaStack Overflow

![](https://cdn.sstatic.net/Sites/stackoverflow/Img/apple-touch-icon@2.png?v=73d79a89bded)
](https://stackoverflow.com/questions/35452591/start-request-repeated-too-quickly)
> [How to put your Raspberry Pi server on the internet with ngrok](https://www.techcoil.com/blog/how-to-put-your-raspberry-pi-server-on-the-internet-with-ngrok/)

<!--//--><![CDATA[//><!--
		/*! This file is auto-generated */
		!function(d,l){"use strict";var e=!1,o=!1;if(l.querySelector)if(d.addEventListener)e=!0;if(d.wp=d.wp||{},!d.wp.receiveEmbedMessage)if(d.wp.receiveEmbedMessage=function(e){var t=e.data;if(t)if(t.secret||t.message||t.value)if(!/[^a-zA-Z0-9]/.test(t.secret)){var r,a,i,s,n,o=l.querySelectorAll('iframe[data-secret="'+t.secret+'"]'),c=l.querySelectorAll('blockquote[data-secret="'+t.secret+'"]');for(r=0;r<c.length;r++)c[r].style.display="none";for(r=0;r<o.length;r++)if(a=o[r],e.source===a.contentWindow){if(a.removeAttribute("style"),"height"===t.message){if(1e3<(i=parseInt(t.value,10)))i=1e3;else if(~~i<200)i=200;a.height=i}if("link"===t.message)if(s=l.createElement("a"),n=l.createElement("a"),s.href=a.getAttribute("src"),n.href=t.value,n.host===s.host)if(l.activeElement===a)d.top.location.href=t.value}}},e)d.addEventListener("message",d.wp.receiveEmbedMessage,!1),l.addEventListener("DOMContentLoaded",t,!1),d.addEventListener("load",t,!1);function t(){if(!o){o=!0;var e,t,r,a,i=-1!==navigator.appVersion.indexOf("MSIE 10"),s=!!navigator.userAgent.match(/Trident.*rv:11\./),n=l.querySelectorAll("iframe.wp-embedded-content");for(t=0;t<n.length;t++){if(!(r=n[t]).getAttribute("data-secret"))a=Math.random().toString(36).substr(2,10),r.src+="#?secret="+a,r.setAttribute("data-secret",a);if(i||s)(e=r.cloneNode(!0)).removeAttribute("security"),r.parentNode.replaceChild(e,r)}}}}(window,document);
//--><!]]>

> [Using Config Files with Ngrok](https://lornajane.net/posts/2018/using-config-files-with-ngrok)

<!--//--><![CDATA[//><!--
		/*! This file is auto-generated */
		!function(d,l){"use strict";var e=!1,o=!1;if(l.querySelector)if(d.addEventListener)e=!0;if(d.wp=d.wp||{},!d.wp.receiveEmbedMessage)if(d.wp.receiveEmbedMessage=function(e){var t=e.data;if(t)if(t.secret||t.message||t.value)if(!/[^a-zA-Z0-9]/.test(t.secret)){var r,a,i,s,n,o=l.querySelectorAll('iframe[data-secret="'+t.secret+'"]'),c=l.querySelectorAll('blockquote[data-secret="'+t.secret+'"]');for(r=0;r<c.length;r++)c[r].style.display="none";for(r=0;r<o.length;r++)if(a=o[r],e.source===a.contentWindow){if(a.removeAttribute("style"),"height"===t.message){if(1e3<(i=parseInt(t.value,10)))i=1e3;else if(~~i<200)i=200;a.height=i}if("link"===t.message)if(s=l.createElement("a"),n=l.createElement("a"),s.href=a.getAttribute("src"),n.href=t.value,n.host===s.host)if(l.activeElement===a)d.top.location.href=t.value}}},e)d.addEventListener("message",d.wp.receiveEmbedMessage,!1),l.addEventListener("DOMContentLoaded",t,!1),d.addEventListener("load",t,!1);function t(){if(!o){o=!0;var e,t,r,a,i=-1!==navigator.appVersion.indexOf("MSIE 10"),s=!!navigator.userAgent.match(/Trident.*rv:11\./),n=l.querySelectorAll("iframe.wp-embedded-content");for(t=0;t<n.length;t++){if(!(r=n[t]).getAttribute("data-secret"))a=Math.random().toString(36).substr(2,10),r.src+="#?secret="+a,r.setAttribute("data-secret",a);if(i||s)(e=r.cloneNode(!0)).removeAttribute("security"),r.parentNode.replaceChild(e,r)}}}}(window,document);
//--><!]]>
[

How to keep ngrok running even when signing off of a server

I have ngrok running on a server I remote into. I start it by using the obvious, ngrok.exe http 80. The problem is that when I sign off on that particular server, ngrok will close out and I will l...

![](https://cdn.sstatic.net/Sites/stackoverflow/Img/apple-touch-icon.png?v=c78bd457575a)YushaStack Overflow

![](https://cdn.sstatic.net/Sites/stackoverflow/Img/apple-touch-icon@2.png?v=73d79a89bded)
](https://stackoverflow.com/questions/50681671/how-to-keep-ngrok-running-even-when-signing-off-of-a-server)
> [How to create a SSH Tunnel with ngrok on Ubuntu Server (aka ssh access to your local server in local network with dynamic ip)](https://diegocarrasco.com/how-to-create-a-ssh-tunnel-with-ngrok-on-ubuntu-server-aka-ssh-access-to-your-local-server-in-local-network-with-dynamic-ip/)

<!--//--><![CDATA[//><!--
		/*! This file is auto-generated */
		!function(d,l){"use strict";var e=!1,o=!1;if(l.querySelector)if(d.addEventListener)e=!0;if(d.wp=d.wp||{},!d.wp.receiveEmbedMessage)if(d.wp.receiveEmbedMessage=function(e){var t=e.data;if(t)if(t.secret||t.message||t.value)if(!/[^a-zA-Z0-9]/.test(t.secret)){var r,a,i,s,n,o=l.querySelectorAll('iframe[data-secret="'+t.secret+'"]'),c=l.querySelectorAll('blockquote[data-secret="'+t.secret+'"]');for(r=0;r<c.length;r++)c[r].style.display="none";for(r=0;r<o.length;r++)if(a=o[r],e.source===a.contentWindow){if(a.removeAttribute("style"),"height"===t.message){if(1e3<(i=parseInt(t.value,10)))i=1e3;else if(~~i<200)i=200;a.height=i}if("link"===t.message)if(s=l.createElement("a"),n=l.createElement("a"),s.href=a.getAttribute("src"),n.href=t.value,n.host===s.host)if(l.activeElement===a)d.top.location.href=t.value}}},e)d.addEventListener("message",d.wp.receiveEmbedMessage,!1),l.addEventListener("DOMContentLoaded",t,!1),d.addEventListener("load",t,!1);function t(){if(!o){o=!0;var e,t,r,a,i=-1!==navigator.appVersion.indexOf("MSIE 10"),s=!!navigator.userAgent.match(/Trident.*rv:11\./),n=l.querySelectorAll("iframe.wp-embedded-content");for(t=0;t<n.length;t++){if(!(r=n[t]).getAttribute("data-secret"))a=Math.random().toString(36).substr(2,10),r.src+="#?secret="+a,r.setAttribute("data-secret",a);if(i||s)(e=r.cloneNode(!0)).removeAttribute("security"),r.parentNode.replaceChild(e,r)}}}}(window,document);
//--><!]]>
[

Speedtest CLI - Internet connection measurement for developers

Speedtest CLI brings the trusted technology and global server network behind Speedtest to the command line.

![](https://www.speedtest.net/s/images/speedtest/favicon/favicon@2x.png)Internet connection measurement for developers

![](https://www.ookla.com/s/images/ookla/OG_image_ookla.png)
](https://www.speedtest.net/apps/cli)[

How do I reboot at a specific time?

Is it possible to re-boot my Raspberry Pi at midnight each night? I know in Linux, you’d use crontab, but I can’t seem to find /etc/crontab.

![](https://cdn.sstatic.net/Sites/raspberrypi/Img/apple-touch-icon.png?v=44fb65dae272)PhorceRaspberry Pi Stack Exchange

![](https://cdn.sstatic.net/Sites/raspberrypi/Img/apple-touch-icon@2.png?v=38b7cb40765d)
](https://raspberrypi.stackexchange.com/questions/2150/how-do-i-reboot-at-a-specific-time)[

arevindh/pihole-speedtest

Pihole Speedtest Mod. Contribute to arevindh/pihole-speedtest development by creating an account on GitHub.

![](https://github.githubassets.com/favicons/favicon.svg)arevindhGitHub

![](https://avatars1.githubusercontent.com/u/693151?s=400&amp;v=4)
](https://github.com/arevindh/pihole-speedtest/wiki/Installing-Speedtest-Mod)[

arevindh/pihole-speedtest

Pihole Speedtest Mod. Contribute to arevindh/pihole-speedtest development by creating an account on GitHub.

![](https://github.githubassets.com/favicons/favicon.svg)arevindhGitHub

![](https://avatars1.githubusercontent.com/u/693151?s=400&amp;v=4)
](https://github.com/arevindh/pihole-speedtest/wiki/Installing-Speedtest-Mod)[

Speedtest CLI - Internet connection measurement for developers

Speedtest CLI brings the trusted technology and global server network behind Speedtest to the command line.

![](https://www.speedtest.net/s/images/speedtest/favicon/favicon@2x.png)Internet connection measurement for developers

![](https://www.ookla.com/s/images/ookla/OG_image_ookla.png)
](https://www.speedtest.net/apps/cli)[

How to Clone Your Raspberry Pi SD Card for Foolproof Backup

Raspberry Pis can be fickle. If you’ve ever gotten a corrupt SD card from a power outage, bad cable, overclocking, or other issue, you know how annoying it can be to start from scratch. But we can fix that.

![](https://www.howtogeek.com/public/images/x192x192.png.pagespeed.gp+jp+jw+pj+ws+js+rj+rp+rw+ri+cp+md.ic.YibPJ1vhGF.png)Whitson GordonHow-To Geek

![](https://www.howtogeek.com/thumbcache/2/200/197a33c6cc0f75617e1591bc63bc0dfa/wp-content/uploads/2018/02/shutterstock_193555763.jpg)
](https://www.howtogeek.com/341944/how-to-clone-your-raspberry-pi-sd-card-for-foolproof-backup/)
[https://c.speedtest.net/speedtest-servers-static.php](https://c.speedtest.net/speedtest-servers-static.php)

[https://dbl.oisd.nl](https://dbl.oisd.nl)
[

Display remains white after kernel update · Issue #223 · goodtft/LCD-show

After installing a full-upgrade as part of a maintenance, the display i used ./LCD35-Show for remains white. Reinstalling the driver wasn&#39;t helpful, but i know the display is likely to be healt...

![](https://github.githubassets.com/favicons/favicon.svg)goodtftGitHub

![](https://avatars3.githubusercontent.com/u/21034251?s=400&amp;v=4)
](https://github.com/goodtft/LCD-show/issues/223)
> [Raspberry Pi Zero W Digital Photo Frame](https://www.reddit.com/r/raspberry_pi/comments/b7xh0n/raspberry_pi_zero_w_digital_photo_frame/?ref_source=embed&amp;ref=share) from
>       [raspberry_pi](https://www.reddit.com/r/raspberry_pi/)

[

pi3d/pi3d_demos

Demos and support files for pi3d (3D graphics python package for the raspberry pi) - pi3d/pi3d_demos

![](https://github.githubassets.com/favicons/favicon.svg)pi3dGitHub

![](https://avatars0.githubusercontent.com/u/3310711?s=400&amp;v=4)
](https://github.com/pi3d/pi3d_demos/blob/master/PictureFrame2020config.py)
> [Silent boot on Raspbian Stretch in Console Mode](https://scribles.net/silent-boot-on-raspbian-stretch-in-console-mode/)

<!--//--><![CDATA[//><!--
		/*! This file is auto-generated */
		!function(d,l){"use strict";var e=!1,o=!1;if(l.querySelector)if(d.addEventListener)e=!0;if(d.wp=d.wp||{},!d.wp.receiveEmbedMessage)if(d.wp.receiveEmbedMessage=function(e){var t=e.data;if(t)if(t.secret||t.message||t.value)if(!/[^a-zA-Z0-9]/.test(t.secret)){var r,a,i,s,n,o=l.querySelectorAll('iframe[data-secret="'+t.secret+'"]'),c=l.querySelectorAll('blockquote[data-secret="'+t.secret+'"]');for(r=0;r<c.length;r++)c[r].style.display="none";for(r=0;r<o.length;r++)if(a=o[r],e.source===a.contentWindow){if(a.removeAttribute("style"),"height"===t.message){if(1e3<(i=parseInt(t.value,10)))i=1e3;else if(~~i<200)i=200;a.height=i}if("link"===t.message)if(s=l.createElement("a"),n=l.createElement("a"),s.href=a.getAttribute("src"),n.href=t.value,n.host===s.host)if(l.activeElement===a)d.top.location.href=t.value}}},e)d.addEventListener("message",d.wp.receiveEmbedMessage,!1),l.addEventListener("DOMContentLoaded",t,!1),d.addEventListener("load",t,!1);function t(){if(!o){o=!0;var e,t,r,a,i=-1!==navigator.appVersion.indexOf("MSIE 10"),s=!!navigator.userAgent.match(/Trident.*rv:11\./),n=l.querySelectorAll("iframe.wp-embedded-content");for(t=0;t<n.length;t++){if(!(r=n[t]).getAttribute("data-secret"))a=Math.random().toString(36).substr(2,10),r.src+="#?secret="+a,r.setAttribute("data-secret",a);if(i||s)(e=r.cloneNode(!0)).removeAttribute("security"),r.parentNode.replaceChild(e,r)}}}}(window,document);
//--><!]]>

> [Customizing Boot Up  Screen on Raspberry Pi](https://scribles.net/customizing-boot-up-screen-on-raspberry-pi/)

<!--//--><![CDATA[//><!--
		/*! This file is auto-generated */
		!function(d,l){"use strict";var e=!1,o=!1;if(l.querySelector)if(d.addEventListener)e=!0;if(d.wp=d.wp||{},!d.wp.receiveEmbedMessage)if(d.wp.receiveEmbedMessage=function(e){var t=e.data;if(t)if(t.secret||t.message||t.value)if(!/[^a-zA-Z0-9]/.test(t.secret)){var r,a,i,s,n,o=l.querySelectorAll('iframe[data-secret="'+t.secret+'"]'),c=l.querySelectorAll('blockquote[data-secret="'+t.secret+'"]');for(r=0;r<c.length;r++)c[r].style.display="none";for(r=0;r<o.length;r++)if(a=o[r],e.source===a.contentWindow){if(a.removeAttribute("style"),"height"===t.message){if(1e3<(i=parseInt(t.value,10)))i=1e3;else if(~~i<200)i=200;a.height=i}if("link"===t.message)if(s=l.createElement("a"),n=l.createElement("a"),s.href=a.getAttribute("src"),n.href=t.value,n.host===s.host)if(l.activeElement===a)d.top.location.href=t.value}}},e)d.addEventListener("message",d.wp.receiveEmbedMessage,!1),l.addEventListener("DOMContentLoaded",t,!1),d.addEventListener("load",t,!1);function t(){if(!o){o=!0;var e,t,r,a,i=-1!==navigator.appVersion.indexOf("MSIE 10"),s=!!navigator.userAgent.match(/Trident.*rv:11\./),n=l.querySelectorAll("iframe.wp-embedded-content");for(t=0;t<n.length;t++){if(!(r=n[t]).getAttribute("data-secret"))a=Math.random().toString(36).substr(2,10),r.src+="#?secret="+a,r.setAttribute("data-secret",a);if(i||s)(e=r.cloneNode(!0)).removeAttribute("security"),r.parentNode.replaceChild(e,r)}}}}(window,document);
//--><!]]>
[

NautiluX/slide

Simple slideshow showing random images from specified directory - NautiluX/slide

![](https://github.githubassets.com/favicons/favicon.svg)NautiluXGitHub

![](https://avatars0.githubusercontent.com/u/2600004?s=400&amp;v=4)
](https://github.com/NautiluX/slide)[

How To Backup Google Photos To Your Computer With gphotos-sync

gphotos-sync is a command line tool for backing up Google Photos (including separate albums) using the Google Photos Library API, for Linux, macOS and Windows. Use it periodically to grab all newly added photos, keeping a complete Google Photos backup on a server or desktop.

![](https://4.bp.blogspot.com/-C3SXpMZFwoM/WxqOMWPcqBI/AAAAAAAAAr4/q3BlIVZd9BIycvFtwpwee9ho2axmuey1wCLcBGAs/s1600-e120/android-icon-192x192.png)LogixLinux Uprising Blog

![](https://cdn.rawgit.com/logix2/6fb43ed0a1979f24c50857fadc6de3ac/raw/24571f5df3fa6fadeeb0937ffd40ea38c380075f/logo2.svg)
](https://www.linuxuprising.com/2019/06/how-to-backup-google-photos-to-your.html)c[

How to copy file remotely via SSH

![](data:image/x-icon;base64,AAABAAEAEBAQAAEABAAoAQAAFgAAACgAAAAQAAAAIAAAAAEABAAAAAAAgAAAAAAAAAAAAAAAEAAAAAAAAAC/oAAAAAAAAMCpNADCwcYA////AMPCxgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAERERERABERETMzMzAAADMRMzNEMAAAAxEzNERAAAADETM0QURAAAARM0QRFEQAABE0RBERQAAAETNEERRAAAMRMzRERAAAMxEzM1RAAAAzETMzM0AAAzMRMzMzMAADMxEzMzMwAAAjETMzMzMAAAMRMzMzMzAAAxERERERERARH/nwAAgAEAAIABAACAAQAAgAEAAIABAACAAQAAgAEAAIABAACAAQAAgAEAAIABAACAAQAAgAEAAIABAAD/9wAA)Simplified Guide

![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACQAAAAkCAMAAADW3miqAAAABGdBTUEAALGPC/xhBQAAAAFzUkdCAK7OHOkAAAI0UExURUdwTMbBwsbBwsbBwsLBwsXBwsbBwsbBwsbBwsbBwgCgv8TBwsbBwg2iv8bBwqy9wVyvwAihv8bBwgCgv8bBwsbBwsbBwsPBwsbBwpS5wTqqwMrFxsbBwsbBwsbBwhekvwKhv6O8wsbBwsbBwhSjv8TBwsbBwgCgv8bBwgGgvwCgvwCgvwCgvxKjv8bBwsbBwo+4wb3AwtHNztPP0E6twIe2wQCgv8bBwliuwCamv6+9wcbBwgGgv526wTyqwACgvwCgvwShv8DAwgCgv0CrwACgvwCgv1auwACgvwCgvwCgvxOjv5q5wSClv0mswMbBwrS+wnKzwYi3wbO+wsPBwq29wm+ywE2twF2wwACgv8bBwv///wAAAAShv/r6+sfCw/7+/tPQ0Qmiv/Lx8cHAwsPBwhSkwPf29t3a2s7JygukwSOmvxylv/P7/UaswCinwNfW1ubk5OTi4oW3whAQEKu9wmyywZy6wcrHx+7s7fDv70e70dHNzujn58nFxh4eHjKpwPz8/Kfe6fT09Pj8/eDf39XU1CsrKwgICFywwJe5wWpqajW0zReoxbfl7l/D1+H0+FCtwK+9wnm0wTuqwH21wWZmZj4+PrGxsdrx9gQEBIjR3yauyXl5eRCnw5mZmVi/09Dt829vb7q/wnTL3EpKSrS+wkqswJK4wWexwGKxwZOTk4mJiSIiImu6ykNDQ77n7tjr747V43Jycqa8waioqO34++v4+jCyy5vZ5sXq8HSzwbHz8mgAAABldFJOUwCV8KcEKji3/jX9/QkFEKcrso/WHFedpCcpp/Bu3frv+JRA4/bGr2Mx424/HBG1Iaen8PCb8CmJ8PWXYurwtIzwM+w1WEKcxDGewMr5Q7l+8jm3t7c4p6en///////////////+A/LdxAAAAqdJREFUOMt91PVTG0EUB/BAQ5EJaXEoVmBwKNTd3V0um5N4gCgxNOGIAIECwQkOBeru/ee6l9xepDf9/nJzM595++692RMIYIQ8SW9suHj5fKNQEI5QnJ+6My6P79+uPpuRlXGpQBxiwuychKrkmDx6+ODOzVNpGFZ6tSwnm1Hik5UlkpioJqanWjEmcsOtyhwxREm5iXHGZm/DsXDa/tzLbIIodV9coS27DkORGxx5SQxKTokxSouRMzhunNzFh2zb6CxcbZwy8COuEN42ZPE7bPv5kF3NIt0rmwq+7+BB5Gs5W6jvJWN4ENkhe9+KkF/Ci5yy9q6F52hGkxs8iGzRdhJgdISbkV8Zj0hYxk0DMD6GRqAb+qqKRaEyFK3ReH4tckuxT6iiECxjhmWI9jmle/wF6grvm96KILaMQjU8sKkk1saWkZqybCBE9pg1NEV4Vz5YpYPrXs/v1VbU/LYDTbynl6AA4Rx+NyiVSl0rbv1oN1I6O9qdrBN+lXfJJWUS3FTS+v4Rtnnc0MyilnYNAO43A8GQsi71gkjzxmcFbE9MKco3Yw2jYRPQ9/9E5+3ZzX6dU+umAD03C3sKutZ9NERo7moOSVrMBACKt66gdfabggLgx+fFf5HE1wV7980MfDFBQuk/dnNTfxpBTq2GApRJpqAoz/f5fm4EWN+Tgsju4KwAE/386EL3cuS6BJqjF2xiDgRgjZt2eALT4WGy967DCw8E9KdVPMqoh2yh3dVUsZeTWQ7RpbXookzAoczNh6jpaEVJChPS16kwy8iJgJy7dwG/suJuNkSi8rzixFAKDxwshI/Dx+H/BEtL21t67PSF4txyEfPvEaUWZSZE5cSZWijOZWUcKkvILKoRCXhz7Xpt1o0r1UfSBf9Jen1dXX1DFPkLsiltJJL7PE0AAAAASUVORK5CYII=)
](https://www.simplified.guide/ssh/copy-file)[

How to change from default to alternative Python version on Debian Linux - LinuxConfig.org

How to change from default to alternative Python version on Debian Linux

![](https://linuxconfig.org/templates/it_headlines/favicon.ico)adminLinux Tutorials - Learn Linux Configuration

![](https://linuxconfig.org/plugins/system/lazyloadforjoomla/assets/images/blank.gif)
](https://linuxconfig.org/how-to-change-from-default-to-alternative-python-version-on-debian-linux)[

david-poirier-csn/pyheif

Python 3.6+ interface to libheif library. Contribute to david-poirier-csn/pyheif development by creating an account on GitHub.

![](https://github.githubassets.com/favicons/favicon.svg)david-poirier-csnGitHub

![](https://avatars1.githubusercontent.com/u/7286281?s=400&amp;v=4)
](https://github.com/david-poirier-csn/pyheif)
