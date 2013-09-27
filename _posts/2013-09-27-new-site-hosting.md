---
published: true
layout: post
date: 
  "2013-09-27 3:11PM": null
categories: "hosting, sysadmin"
---

#New Site Hosting
I've changed the hosting setup for this site. The change was precipitated by my recent employment changes, and more particularly having to re-key my online accounts with new ssh keys for a new laptop. 
Previously I was hosting this site on Heroku, using Jekyll and git as my blogging platform. You can see the git repository on Github [here](https://github.com/mcondie/alphabit). I used Heroku because it was free, and a Jekyll site doesn't require very much horsepower to serve. 
Once I needed to re-key everything, the upside of Heroku (free) was overwhelmed by my need to control everything, so I've moved the site over to [Digital Ocean](digitalocean.com) on one of their smallest "droplets". 
So far the experience at Digital Ocean has been good. The price ($5 a month) is better than the smallest Linode instance, and the speed seems to be great. I'm planning to move my big application (higher.io) over to an instance in a few weeks for a real comparison between Linode and Digital Ocean, but for now this blog seems to be in a good place.