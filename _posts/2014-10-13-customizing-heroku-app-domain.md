---
layout: post
title: "Creating Custom Domain for Heroku Apps"
date: 2014-10-13 14:24:00
categories: programming
---

So now I have [redmine](http://whispering-garden-6016.herokuapp.com/) up and running on Heroku, it would be really nice for me to direct it to something like wiki.tonyt.me or bugs.tonyt.me.

If it's anything similar to making <http://nflavour.github.io> to point to <http://tonyt.me>, then I should be able to quickly change it in Namecheap's DNS settings and add a CNAME file in the heroku app.

I'm following [this guide](https://devcenter.heroku.com/articles/custom-domains). First look it is fairly long. But I'm going to break it down, so only the necessary part will be summarized.

1.  Login to Namecheap then select `Number of domains in your account    view`

2.  Select the domain you wish to change DNS for

3.  On the sidebar, select `All Host Records` under *Host Management*

4.  On the `Sub-Domain Settings`, add a new entry

    **Host Name** - the subdomain name. For example, wiki.example.com, `wiki` is the host name.

    **IP Address/URL** - the address that the subdomain should direct to. For example, wiki.example.com should show the content on app-123456.heroku.com, `app-123456.heroku.com` is the ip address.

    **Record Type** - CNAME (Alias)

    **TTL (Time to Live)** - The time it takes for a change to refresh. If you don't plan on changing it, use something like 86400. It is measured in seconds, so 86400 is 24 hours. I chose something small for now, just in case I screw something up, I don't need to wait that long. But I will be changing it to 86400.

5.  In terminal, cd to the app's local directory. Then enter `heroku domains:add wiki.example.com`. Replace wiki.example.com with the domain that it is supposed to redirect to.
