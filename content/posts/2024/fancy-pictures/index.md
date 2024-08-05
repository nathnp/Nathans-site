+++
title = 'Fancy Pictures'
date = 2024-07-04T22:06:00-04:00
draft = false
subtitle = "It goes in and out of dark mode"
tags = ['Web']
+++

Over on my [States I've been to](/states) page, I have my flight stats in the form of a passport. This is a image exported from [Flighty](https://flightyapp.com), the flight tracker I use.

As a bit of fun, Flighty has a regular version, and a blacklight version. You get the choice of which one you want to export.

<table class="invisTable">
	<tr>
		<td>
			<figure>
			<img src="/states/PassLight.webp"/>
			<figcaption>Light Mode</figcaption>
			</figure>
		</td>
		<td>
			<figure>
			<img src="/states/PassDark.webp"/>
			<figcaption>Dark Mode</figcaption>
			</figure>
		</td>
	</tr>
</table>

I wanted to have both on my [/states](/states) page. As they both look really cool. So I did some digging. How can I have the images switch, depending on if the readers browser is in light, or dark mode.

After some searching, I found a bit of HTML that looked like it would do what I wanted.

```HTML
<picture>
  <source srcset="PassDark.webp" media="(prefers-color-scheme:dark)">
  <img src="PassLight.webp">
</picture>
```

After implementing it, it worked! And it looks really good as well.

<figure>
	<img src="gif1.gif"/>
</figure>