+++
title = 'New New Site'
date = 2023-11-06T12:44:12-05:00
draft = false
subtitle = 'Now with more static'
tags = ['Web', 'Hugo']
+++

Welp, this was a pain. 

Over the past few days, I have been working on moving my website. Why you might ask? Let's go over that.

For a while, I was hosting this site on [blot.im](https://blot.im). Blot basically takes a bunch of markdown files you send them, and turns them into a website. I was a big fan of this. Simple, easy, and flexible. However, I started running into problems. 

When you send MD files to blot, blot will cache the files, and build a site out of them. Every now and then, that cache would get stuck. You could push new files, but they wouldn't appear on the visible site. The only way I had to force the cache to refresh, was to email the dev.

## Moving to Something New

After some thinking, I decided to go with a static site. I'll generate the site on my mac, then push it to a host. The first tool I tried out was [11ty](https://www.11ty.dev) After a bunch of work, I got a super basic site up and running with [11ty](https://www.11ty.dev) However, I didn't like it. [11ty](https://www.11ty.dev) is written in Java Script, and I really don't like Java Script.

The next tool I tried was [Jekyll](https://jekyllrb.com). Jekyll looked way nicer to work with. There was just one tiny problem. Ruby 3.1.3 didn't want to compile on my mac. So that was out.

The tool that I went with (as you can see in the footer), is [Hugo](https://gohugo.io). Hugo, ships as a Go binary. This fixes the issue I had with Jekyll, and 11ty. Nothing to compile, and it's not Java Script. I'm not going to go into how to use Hugo, as I'm still learning it. 

As for hosting, I'm using [Github Pages](https://pages.github.com). All I have to do, is drop the built site into a folder. and push that to Github.

The best part of all of this. My hosting costs have gone from $4/month, to $0/month.

I'm still not done yet. The main thing remaining to to move all of my old posts over. That's going to take a bit. I'll get there though.