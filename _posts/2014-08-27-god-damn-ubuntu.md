---
layout: post
title: "God Damn Ubuntu"
date: 2014-08-27 21:25
categories: programming other
---
Tried installing Ubuntu alongside Windows 7. Took me all day yesterday, and I still couldn't get it right.

Oh, the installation was the easy part. But even that took hours.

Ubuntu couldn't recognize that Windows 7 was installed in the system. But that's okay, I'm going to install in my secondary drive anyways. But apparently, raid 0 doesn't like Ubuntu. So don't try to install Ubuntu on raid 0 drive. Installation failed and IT BROKE MY RAID... Luckily all the files were backed up.

So 2nd attempt. Without any raid 0. It worked. Updates. Everything looks fine. Except that without the nVidia driver, the display is overscanned. This was an issue on the Windows side too, but it was easily fixed by adjusting the overscan in nVidia controls. So I tried to install nVidia driver the "windows" way, which was to download from nVidia's website. That didn't pan out so well. So I did the "normal" way and tapped into a ppa repository and `apt-get` the drivers.

Then everything went to hell. After installing the drivers, I rebooted into Ubuntu. Blank. Nothing. Black. Hit the reset button, still nothing. Okay, I screwed up the drivers. Reset into Windows. Blank. Nothing. Black. Okay I screwed up my set up. Probably now would be a good time to give up and just reinstall Windows. But I decided to spend about 6 hours to fix the driver issue. I couldn't. I had to reinstall Windows. And I ended up using VirtualBox which works a lot better. I can see my screen.

So, don't install on nVidia cards, or don't install any graphics drivers. Never trying that again.