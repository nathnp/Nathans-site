+++
title = 'Adding Spellcheck'
date = 2024-07-10T17:09:00-04:00
draft = false
subtitle = "Another thing I should have done sooner"
tags = ['Web', 'GitHub']
+++

Like a lot of people, I make typos. I do try to catch them with proof reading, but I still miss a fair number. So I had an idea.

I've been playing around with GitHub workflows recently. So I though, why not have GitHub do a spellcheck pass. This was a bigger headache than I thought. I'm pretty new to GitHub workflows, and my main repo had a lot of typos.

<h2>Just Work Damn You</h2>
<hr>

Getting a working workflow was a pain. It didn't help that search these days is garbage. After a while and lot of tinkering, I found something that worked. [This post](https://www.javierbrea.com/blog/spellcheck-github-action/) from JBREA was just what I was looking for, and it worked.

<h2>That's A Lot Of Typos</h2>
<hr>

The first time the workflow ran on my main repo... It was ugly. Like, really ugly. Yeah, there was a lot of false positives, but also a lot of actual typos. I spent a few hours working on that. Adding the false positives to a custom word list, and fixing the real typos.

Right now I just have it set up to notify me if it finds something[^1]. I might set things up so the site build only happens, if the spellchecker passes. That would stop a typo from going live. I might play around with that, it's a good excuse to learn GitHub workflows more.

[^1]: I have to workflow in both my draft, and live repo.