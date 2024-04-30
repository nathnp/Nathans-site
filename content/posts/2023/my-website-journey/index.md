+++
title = 'My Website Journey'
date = 2023-11-12T01:07:04-05:00
draft = false
tags = ['Web']
+++

I've had a blog for a few years now. And over those few years, I've used a number of different hosting providers.

As I've recently moved to a new blogging set up. I decided, let's take a look back. At how I used to host this site.

### Write.as

<aside>
	During this time, my blog was on <code>blog.sulairris.com</code>
</aside>

I started out my blogging adventure using Write.as. Write.as made getting started super easy. I made an account, and boom, I had a blog. For only $9/month.

Write.as was pretty good. However, It's pretty limited on customization. After a couple of years on it, I started looking around at other options.

### Wordpress

<aside>
	When moving to Wordpress, I moved my site to just <code>sulairris.com</code>
</aside>

I decided to go over to Wordpress. This move started with setting up an account on Wordpress.com. This didn't last long. As they never got my SSL cert set up. I ended up running Wordpress on a Debian VM. That VM, was one of Linode's Nanode VMs. The Nanode is a super tiny VM, that only costs $5/month. 

<aside>
	I later rebuilt my site under a new domain, <code>nthp.me</code>
</aside>

Wordpress starting getting on my nerves pretty quick. Wordpress is very, very good, at getting in the way. Over time, this just got more, and more, annoying. Around this time as well, I want to be able to post from my phone. Wordpress had a mobile app, neat. That app however, needed a plugin installed. A plugin that wanted a Wordpress.com account... No.

### Blot

<aside>
	I used to have a second RSS only blog on Blot, at <code>rss.nthp.me</code>
</aside>

With wanting a more easy way to post from my phone, and less overhead. I started looking around at web hosts again. After seeing a post from [Kev](https://kevquirk.com/moving-from-jekyll-to-blot), I decided to check out blot. Blot very quickly got my attention. Everything is done in Markdown, and synced over Git. This meant that I didn't have to deal with Wordpress. I could also post from my phone using a mobile Git client. Neat. And the cherry on top, it was only $4/month. One dollar less than Linode. However, I started running into a problem.

When you send MD files to blot, blot will cache the files, and build a site out of them. Every now and then, that cache would get stuck. You could push new files, but they wouldn't appear on the visible site. The only way I had to force the cache to refresh, was to email the dev. This made me start looking again.

### The Present 

I'm not going into all the different tools I looked at. That can be a whole blog post on it's own. And I already kinda wrote it. You can read that [here](https://nthp.me/posts/new-new-site/). This site, is using three main components. Hugo, Simple.CSS, and Github Pages. Hugo is what generates my site. When I want to make a post. I write it as an MD file. Then I have have Hugo generate the entire website. Boom, website.

By default, that website would look, kinda bad. To make the site site look better, I use Simple.CSS. Simple.CSS is great for two main reasons. 1. It look pretty good and professional. And 2. I don't have to learn CSS to use it, and that makes my happy.

Unlike with the previous systems. That fancy site I made, lives only on my Mac... That's... kinda an issue. Lucky I had a couple of options. I ended up going with Github Pages, as I already use Github, and it's free. Yep, free static site hosting. This dropped my costs for my blog from $4/month, to nothing.

### Thoughts On All This

I've moved around a lot. And because of that, I've learned a lot. I've learned of a number of good hosts. How to spin up a Wordpress VM in the cloud. A number of static site generator tools. And started learning about Github Actions. But, my favorite thing I've learned from all this. Is how to set up a fully featured site / blog, for free.