---
title: How to Change DNS Provider on Windows
slug: how-to-change-your-dns-provider-on-windows
date: 2020-08-05T02:37:12.000Z
date_updated: 2020-08-05T02:42:00.000Z
tags: code, windows
excerpt: How best to change your DNS provider on Windows 10 to use a service like Pi-Hole, Cloudflare or Google DNS.
---

I've been mainly a OSX guy since I think Windows 95. Maybe I made to Windows 98 so my memory of how to do stuff on Windows is a bit rusty. 

Recently I setup PiHole and for some reason my gaming PC wasn't showing as using Pi-Hole as a DNS provider despite setting it as the provider in my router. It turned out years ago I changed it manually to cloudflare and forgot how to do it. So this post is more than anything a reminder of how to do it and may be of use to you.

*Note: [Pi-Hole](https://pi-hole.net/) is a way to block ads at the DNS level on your home network. It's great and works on even the oldest Raspberry Pi's. [Check it out](https://pi-hole.net/). *

Ok, so this is what you gotta do to change your DNS. 

1. In the search type in `Network Connections` and then go to the top result. 
2. Right click on whatever device you use to connect to the internet and select `Properties`
3. Double click on "Internet Protocol Version 4" and on the bottom edit your DNS's servers as needed to whatever you want, be it your Pi-Hole or Cloudflare's `1.1.1.1`
4. Do the same for Version 6 if needed
5. Enjoy!
