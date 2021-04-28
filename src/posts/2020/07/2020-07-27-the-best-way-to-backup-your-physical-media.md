---
title: The Best Way to Backup Your BluRays, DVDs and other Physical Media
slug: the-best-way-to-backup-your-physical-media
date: 2020-07-28T02:18:33.000Z
date_updated: 2020-09-18T15:12:11.000Z
tags: code, how-to
excerpt: The best way to backup your personal collection of BluRay's and DVDs to reclaim some shelf space using MakeMKV and Other Transcode.
---

If you have a number of old BluRay's and DVD's that you can legally back-up I found what I believe to be the best way to back them up to a hard drive and preserve a very good quality viewing experience at the same time so you can move your old disks to the Attic for safe keeping. 

I will take you through my process, and how best to go about the process.

## Hardware

In addition to your own BluRay's and DVD's you will need a BluRay drive in the the linked [list](https://www.makemkv.com/forum/viewtopic.php?f=19&amp;t=18856). 

If you have one of these great! This will be easy. If not you can buy one from Amazon, EBay, Craiglist etc.. You can typically find one from $50-$100. The reason you need one of these drives is because of LibreDrive. What's [LibreDrive](https://www.makemkv.com/forum/viewtopic.php?f=19&amp;t=18856), well i'll let the creator of MakeMKV tell you:

> A LibreDrive is a mode of operation of an optical disc drive (DVD, Blu-ray or UHD) when the data on the disc are accessed directly, without any restrictions or transformations enforced by drive firmware. A LibreDrive would never refuse to read the data from the disc or declare itself “revoked”.

> Please note that LibreDrive mode is not about hacking or meddling with AACS code. In LibreDrive mode the updated software communicates to the drive hardware directly, not touching or hacking AACS DRM code in any way at all. So your drive will continue to self-revoke on MKB updates and require authentication before releasing key material to the "authorized" software - it is just with LibreDrive mode all of it is no longer relevant.

What this is saying is that by using LibreDrive to backup your media you aren't hacking any DRM. You aren't cracking their  code or anything like that. You are merely having the BluRay drive you own access part of the disk on the BluRay or DVD that you own as well that you normally wouldn't be able to. The logic sounds so simple but this method of accessing data is truly genius. I don't know the minds that developed this, but they are operating on another level.

## Software Part 1 | MakeMKV

After you get the drive sorted the next thing you need is to download [MakeMKV](https://www.makemkv.com/) and install it. Both Windows and Mac work. The software is shareware, so you can use it for free, but if you find you are using it a lot please consider purchasing it so the developer can continue to dedicate time to making it better.

Once downloaded open it up and install it, once open put in your first BluRay disk and hit scan. What it will do is find all the files on the drive and give you the option what you want to save. A typical file would have the feature film as the largest file followed by a number of smaller files that may be extra's. It's up to you if you want to save them or not.

Name the file and its off to the races! If the disk is clean (read not scratched up) I get anywhere from a 4x to 6x read. So a 2 hour film may take 30:00 to save. 

Once it's done you will have something like a 20gb (or larger) MKV file that is playable in most software. You may have the hard drive space for this, and if that's the  case you are all done! Congrats you backed up your owned media! 

But lets say you want to shrink that file down quickly and without much quality loss. You could of course use Handbrake, but the following is a MUCH better method.

## Software Part 2 | Other Transcode

[Other Transcode](https://github.com/donmelton/other_video_transcoding) is a compact Ruby script written by [Don Melton](https://donmelton.com/), yes that Don Melton. The person who started Safari and Webkit. It turns out he is just like us and doesn't want to have a mountain of films in his living room. He wrote a fantastic script that I have used without fail for a long time. 

He wrote up a FANTASTIC installation guide. I'll let you get that setup, come back when your done.

.

.

All done! Ok. Now comes  the fun part, seeing just how rocking fast this converter is.  This is the command I use. I will break down each part of it.

`other-transcode --crop auto --add-subtitle eng --burn-subtitle auto --nvenc-temporal-aq "D:\Video\FilmName\FilmName.mkv"`

`other-transcode` - This of course calls the software
`crop auto` - This takes away the black baars from the top and bottom. If you are just going to play films on a 16:9 TV this isn't really needed but if you have an Ultrawide computer monitor or expect TVs to change in shape in the future this is a must. My recommendation is to use it.
`add-subtitle eng` - This is an easy one, I want English subtitles on its own track.
`burn-subtitle auto` - This is a bit more nuanced. It burns subtitles in the movie on the video. For example if someone is speaking Russian in an otherwise English movie this would preserve the captions that translate it.
``nvenc-temporal-aq`` - Now this is fun one. This leverages my video card (a 1070) to do the heavily lifting of decode and encode. This is what makes the conversion EXTREMELY fast and the quality extremely good. There are tons of other options if you have an AMD card, want to convert to HEVC vs H264 or what to use full temperal AQ. Again Don has documented it very well [here](https://github.com/donmelton/other_video_transcoding/wiki/Video).
`"D:\Video\FilmName\FilmName.mkv"` - Finally this is the where the film is located. 

One thing to be aware of is the folder that you are in, say `C:\Users\Dan` is where the video will save, so if you have say a Plex folder, you may want to navigate there before running the above command. 

When I do this here are my average results for a 1080p BluRay on a 7700K (a tad overclocked) with a NVIDIA 1070 writing to 2 IronWolf NAS drive's using Window's Storage Pools. (I am more disk speed bound than anything. If I was pure NVMe drives this would be even faster.)

## Sample BluRay
InputOutputReduction25 GB5.72 GB4.4XConverting at: 262 FPS, 10.8X
## Sample DVD
InputOutputReduction4.99 GB1.92 GB2.6XConverting at: 1,374 FPS, 57.3X
All in I spend *MAYBE* 5 minutes of actual time clicking, naming, moving folders to get from BluRay to file in my Plex library. I could even automate more of it, so that once the MakeMKV job finishes is auto-runs the `other-transcode` script but I like doing a bit of QA before start that to make sure the backup looks good. I am not sure why I do that, it has always came out good.

Hopefully this is something you will try out and find success and joy with, and if you do please let me know on Twitter. 
