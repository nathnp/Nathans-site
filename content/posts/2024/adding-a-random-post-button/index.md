+++
title = 'Adding a Random Post Button'
date = 2024-07-18T10:12:00-04:00
draft = false
subtitle = "Where will it take me?"
tags = ['Web', 'Hugo']
+++

I've seen a number of sites that have a random post button. A button that when you click it, you get shot to a random post. Seeing how I might have spoken a bit too soon about getting over a cold, and have nothing to do, I decided to add one. The only issue is, this is a static site, and I hate JavaScript.

## I Command You To Be Random

---

Not wanting to use JavaScript, left me with one option. I'd have to bake the link in at build time. After a little playing around, I settled on a simple three lines of Hugo.

```GO
  {{ $pages := where .Site.RegularPages "Section" "posts" -}}
  {{- $randomPage := index (shuffle $pages) 0 -}}
  <a href="{{ $randomPage.Permalink }}">Random Post</a>
```

All this does, is generate a list of all of my posts, shoves that into a variable, shuffles that in to a new variable, and prints a link with the first item.

While this works well, the link will only be random at build time. After that, it's just a normal link. That goes for all random links. I have two at the moment, and because the link is random per function, they both go to different posts.

To mitigate the whole “only random at build time”, I’ve add cron line to my GitHub workflow. This will rebuild the site everyday at 00:00UTC. That’ll help keep things fresh.

```yml
schedule: [{cron: "0 0 * * *"}]
```