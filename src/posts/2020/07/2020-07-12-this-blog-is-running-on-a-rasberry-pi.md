---
title: This Blog is Running on a Rasberry Pi
slug: this-blog-is-running-on-a-rasberry-pi
date: 2020-07-12T20:19:07.000Z
date_updated: 2020-07-13T16:18:25.000Z
tags: code
---

First things first. Click around this site a bit. Pretty speedy right? You wouldn't think that possible on a Raspberry Pi on a home internet connection. Well with the proper caching anything is possible! Additionally, I didn't have to poke any holes through my firewall. Only one service can get to my Pi, and that's Cloudflare. This makes it performant and secure.

## First things first

- You will need a Raspberry Pi, I have a Pi4 with 4gb of ram. This is overkill, but I had it leftover from a digital signage project. Any Pi4 should do. 
- Flash the SD card with the latest version of Ubuntu Server. If you need help they provide a fantastic getting started guide [here](https://ubuntu.com/tutorials/how-to-install-ubuntu-on-your-raspberry-pi).
- Power it up run it over ethernet. You can get it working with Wireless but it won't perform at its best.
- SSH in to the IP address your home router assigned to the pi: `ssh ubuntu@192.168.1.5`
- Change your password into something secure
- Update packages with `sudo apt update` and `sudo apt upgrade` and then restart the Pi and log back in.	
- Set up a free account at [Cloudflare](https://www.cloudflare.com) and if you are ready to point your domain/subdomain to your Pi update nameservers.

## Set up NGINX

- Install: `sudo apt install nginx`
- Enable proper firewall rules: `sudo ufw allow 'Nginx Full'`
- Confirm status: `sudo ufw status`

## Get Cloudflared Running

- Now for the fun stuff. Lets get NGINX and Cloudflared installed but first we need Go a programming language from Google by using this command: `sudo apt-get install golang`
- Now grab the latest version of Cloudflared: `go install github.com/cloudflare/cloudflared/cmd/cloudflared`
- Check that its installed with `cloudflared — version` you should see something like this in response: cloudflared version 2020.7.1
- Now you login with Cloudflare: `cloudflared tunnel login`  in your normal computer browser, you don't; have to do with your Pi and pick the domain you want to have tunneled. Once this is done the cert shoud auto apply.
- Test that you have it working with a default site by running this command: `cloudflared — hostname yourdomainname.com  [http://localhost:80](http://localhost:8000/)`  after a minute or two your domain name should resolve to the default NGINX site. 
- Congrats you are now tunneling traffic from the general web, through Cloudfare directly to your Pi. With all the protections and speed benefits offered by Cloudflare.

## Ghost Setup
[

How to install & setup Ghost on Ubuntu 16.04 + 18.04

A full production install guide for how to install the Ghost professional publishing platform on a production server running Ubuntu 16.04 or 18.04.

![](https://ghost.org/icons/icon-512x512.png?v=e58c97d95fb227a34fe36491b7d4a4c9)GhostGhost

![](https://ghost.org/images/meta/Ghost-Docs.jpg)
](https://ghost.org/docs/install/ubuntu/)
Ghost has provided excellent documentation here. Follow their guide and come back here.

You will not be able to preview your Ghost install in a browser, just make sure Ghost is running on the Pi itself. You can verify this with `ghost status` and possible fix issues with `ghost doctor`.

## Tie It All Together

Now that you have Ghost and Cloudflared running you need to tie the 2 together and run Cloudflared as a service.

- To start the service up and running follow this

[

Automatically Starting Argo Tunnel

A collection of documentation for Cloudflare products.

![](https://www.cloudflare.com/img/favicon/apple-touch-icon.png)Cloudflare Developer Docs

](https://developers.cloudflare.com/argo-tunnel/reference/service/)
- Don't forget copying the cert to `/etc/cloudflared`
- Set up your `config.yml` file by creating a new file in the cloudflared folder and putting data such as this.

    hostname: tunnel.yourdomain.com
    url: https://localhost:2368
    logfile: /var/log/cloudflared.log
    

- Make sure the port number matches the port number you get back from `ghost status`
- Restart the service `systemctl service restart cloudflared`
- Wait about a minute, and if all is well you should see the default Ghost site show up on your custom domain name! Voila!
- Navigate over to yourdomain.com/ghost and set up an initial user
- Enjoy!

That is really all there is to it. It sounds like a lot, but not counting package installion time this takes about 3o minutes and provides a pretty high performance little website that you have full control over for no cost!  I hope you enjoyed this, please reach out on Twitter if you have any questions.

## Help Commands

If you get stuck, these commands may help:

`systemctl status nginx` this tells you the current status of NGINX

`sudo systemctl stop nginx` stops NGINX, you can also replace stop with `start`, `reload`, `restart`, `disable`, and `enable`.

`journalctl -xe` view log entries of most recent Cloudflared activity

`ghost status` report on Ghost's status.

If you have to copy the cert from your personal computer to the Pi. Open a new terminal window and use a command like this: `scp cert.pem [ubuntu@192.168.1.](ubuntu@192.168.1.)5:/etc/cloudflared` to copy the cert from your computer to the Pi.

## **Sources**
[

Self Hosting with Raspberry Pi and Argo Tunnels

With all the cloud solutions on the market, self hosting has become a hobby for the extra nerdy. Why bother with all the port forwarding, securty implications, ISPs, and reliability headaches that…

![](https://cdn-images-1.medium.com/fit/c/152/152/1*8I-HPL0bfoIzGied-dzOvA.png)NickMedium

![](https://miro.medium.com/freeze/max/1200/1*0pwn6K9xvROx3jZtZACRVA.gif)
](https://medium.com/@durksauce/self-hosting-with-raspberry-pi-and-argo-tunnels-11f06d1309a9)[

How To Install Nginx on Ubuntu 20.04 | DigitalOcean

Nginx is one of the most popular web servers in the world and is responsible for hosting some of the largest and highest-traffic sites on the internet. In this guide, we’ll discuss how to get Nginx installed on your Ubuntu 20.04 server.

![](https://www.digitalocean.com/assets/community/android-icon-192x192-4d13e6664f412f6904a78be76d626004bcbbd59671f6c755919628134003c2a8.png)Erin GlassDigitalOcean

![](https://community-cdn-digitalocean-com.global.ssl.fastly.net/assets/tutorials/images/large/nginx_install_updated_logo.png?1587673882)
](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-20-04)[

How to start, stop, and restart services in Linux

The process of starting and stopping services in Linux is not that complicated. Jack Wallen shows you how easily it can be done.

![](https://tr2.cbsistatic.com/fly/bundles/techrepubliccore/logo-192x192.png)Jack WallenTechRepublic

![](https://tr4.cbsistatic.com/hub/i/r/2017/03/15/b6212a24-048d-42c1-993f-a320353e60f6/thumbnail/770x578/0af1f6d16479c68cd65643a00e182793/sysctlhero.jpg)
](https://www.techrepublic.com/article/how-to-start-stop-and-restart-services-in-linux/)[

How To Use Systemctl to Manage Systemd Services and Units | DigitalOcean

Systemd is an init system and system manager that is widely becoming the new standard for Linux machines. While there is considerable controversy as to whether systemd is an improvement over the init systems it is replacing, the majority of distributions are either...

![](https://www.digitalocean.com/assets/community/android-icon-192x192-4d13e6664f412f6904a78be76d626004bcbbd59671f6c755919628134003c2a8.png)Justin EllingwoodDigitalOcean

![](https://community-cdn-digitalocean-com.global.ssl.fastly.net/assets/tutorials/images/large/Systemctl_tw.png?1426699814)
](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units)[

How to copy file remotely via SSH

![](data:image/x-icon;base64,AAABAAEAEBAQAAEABAAoAQAAFgAAACgAAAAQAAAAIAAAAAEABAAAAAAAgAAAAAAAAAAAAAAAEAAAAAAAAAC/oAAAAAAAAMCpNADCwcYA////AMPCxgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAERERERABERETMzMzAAADMRMzNEMAAAAxEzNERAAAADETM0QURAAAARM0QRFEQAABE0RBERQAAAETNEERRAAAMRMzRERAAAMxEzM1RAAAAzETMzM0AAAzMRMzMzMAADMxEzMzMwAAAjETMzMzMAAAMRMzMzMzAAAxERERERERARH/nwAAgAEAAIABAACAAQAAgAEAAIABAACAAQAAgAEAAIABAACAAQAAgAEAAIABAACAAQAAgAEAAIABAAD/9wAA)Simplified Guide

![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACQAAAAkCAMAAADW3miqAAAABGdBTUEAALGPC/xhBQAAAAFzUkdCAK7OHOkAAAI0UExURUdwTMbBwsbBwsbBwsLBwsXBwsbBwsbBwsbBwsbBwgCgv8TBwsbBwg2iv8bBwqy9wVyvwAihv8bBwgCgv8bBwsbBwsbBwsPBwsbBwpS5wTqqwMrFxsbBwsbBwsbBwhekvwKhv6O8wsbBwsbBwhSjv8TBwsbBwgCgv8bBwgGgvwCgvwCgvwCgvxKjv8bBwsbBwo+4wb3AwtHNztPP0E6twIe2wQCgv8bBwliuwCamv6+9wcbBwgGgv526wTyqwACgvwCgvwShv8DAwgCgv0CrwACgvwCgv1auwACgvwCgvwCgvxOjv5q5wSClv0mswMbBwrS+wnKzwYi3wbO+wsPBwq29wm+ywE2twF2wwACgv8bBwv///wAAAAShv/r6+sfCw/7+/tPQ0Qmiv/Lx8cHAwsPBwhSkwPf29t3a2s7JygukwSOmvxylv/P7/UaswCinwNfW1ubk5OTi4oW3whAQEKu9wmyywZy6wcrHx+7s7fDv70e70dHNzujn58nFxh4eHjKpwPz8/Kfe6fT09Pj8/eDf39XU1CsrKwgICFywwJe5wWpqajW0zReoxbfl7l/D1+H0+FCtwK+9wnm0wTuqwH21wWZmZj4+PrGxsdrx9gQEBIjR3yauyXl5eRCnw5mZmVi/09Dt829vb7q/wnTL3EpKSrS+wkqswJK4wWexwGKxwZOTk4mJiSIiImu6ykNDQ77n7tjr747V43Jycqa8waioqO34++v4+jCyy5vZ5sXq8HSzwbHz8mgAAABldFJOUwCV8KcEKji3/jX9/QkFEKcrso/WHFedpCcpp/Bu3frv+JRA4/bGr2Mx424/HBG1Iaen8PCb8CmJ8PWXYurwtIzwM+w1WEKcxDGewMr5Q7l+8jm3t7c4p6en///////////////+A/LdxAAAAqdJREFUOMt91PVTG0EUB/BAQ5EJaXEoVmBwKNTd3V0um5N4gCgxNOGIAIECwQkOBeru/ee6l9xepDf9/nJzM595++692RMIYIQ8SW9suHj5fKNQEI5QnJ+6My6P79+uPpuRlXGpQBxiwuychKrkmDx6+ODOzVNpGFZ6tSwnm1Hik5UlkpioJqanWjEmcsOtyhwxREm5iXHGZm/DsXDa/tzLbIIodV9coS27DkORGxx5SQxKTokxSouRMzhunNzFh2zb6CxcbZwy8COuEN42ZPE7bPv5kF3NIt0rmwq+7+BB5Gs5W6jvJWN4ENkhe9+KkF/Ci5yy9q6F52hGkxs8iGzRdhJgdISbkV8Zj0hYxk0DMD6GRqAb+qqKRaEyFK3ReH4tckuxT6iiECxjhmWI9jmle/wF6grvm96KILaMQjU8sKkk1saWkZqybCBE9pg1NEV4Vz5YpYPrXs/v1VbU/LYDTbynl6AA4Rx+NyiVSl0rbv1oN1I6O9qdrBN+lXfJJWUS3FTS+v4Rtnnc0MyilnYNAO43A8GQsi71gkjzxmcFbE9MKco3Yw2jYRPQ9/9E5+3ZzX6dU+umAD03C3sKutZ9NERo7moOSVrMBACKt66gdfabggLgx+fFf5HE1wV7980MfDFBQuk/dnNTfxpBTq2GApRJpqAoz/f5fm4EWN+Tgsju4KwAE/386EL3cuS6BJqjF2xiDgRgjZt2eALT4WGy967DCw8E9KdVPMqoh2yh3dVUsZeTWQ7RpbXookzAoczNh6jpaEVJChPS16kwy8iJgJy7dwG/suJuNkSi8rzixFAKDxwshI/Dx+H/BEtL21t67PSF4txyEfPvEaUWZSZE5cSZWijOZWUcKkvILKoRCXhz7Xpt1o0r1UfSBf9Jen1dXX1DFPkLsiltJJL7PE0AAAAASUVORK5CYII=)
](https://www.simplified.guide/ssh/copy-file)
