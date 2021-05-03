---
title: Remotely Monitoring Raspberry Pi System Vitals
slug: remotely-monitoring-raspberry-pi-system-vitals
date: 2020-07-13T17:25:45.000Z
date_updated: 2020-10-06T20:19:20.000Z
tags: code
excerpt: Setup and run Glances to monitor your Raspberry Pi's vitals from any web browser.
---

A little 4 core Raspberry Pi may not really need any big time monitoring. Especially if the web server is running through Cloudflare, but sometimes it is nice to just have a at a glance view of CPU, Memory, Processes, etc.. The easiest way of monitoring that I have found is via [Glances](https://nicolargo.github.io/glances/). This is how I setup and use it on my Raspberry Pi web server.

Firstly, install Glances: `sudo apt install glances`

Verify its working with `glances -w`

Now set it up as a service by creating the following file: `sudo nano /usr/lib/systemd/system/glancesweb.service`

and editing with the following information:

    [Unit]
    Description = Glances in Web Mode
    After = network.target
    
    [Service]
    User=pi
    ExecStart = /usr/bin/glances  -w  -t  10
    Restart=always
    
    [Install]
    WantedBy = multi-user.target
    

The `10` there is  the refresh interval. You can set it whatever you needs are. I like 10 seconds as the information doesn't have to be up to the second for my needs.

Enable the service: `sudo systemctl enable glancesweb.service`
Start the service: `sudo systemctl start glancesweb.service`
Verify the service is running: `sudo systemctl status glancesweb.service`

And then navigate to the dashboard in your computers web browser and enjoy the complete look at your Pi's vitals.
![](/assets/img/posts/2020/07/Screenshot_2020-07-13-ubuntu---Glances.png)
