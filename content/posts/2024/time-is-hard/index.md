+++
title = 'Time Is Hard'
date = 2024-04-20T12:16:35-04:00
draft = false
subtitle = "Yesterday was one year ago"
tags = ['Web', 'Hugo']
+++

I feel like the idea of having to put a disclaimer on a post that it's old, is a bad sign. The simple fact that a number of people need a big sign saying "This post is old", is kinda depressing. And the worst part, it's not a bad idea.

This post isn't going to be about that, its going to be about how much I hate writing functions to handle time.

<h2>Yesterday was last year</h2>
<hr>

My plan was simple, if a post is over a year old, have Hugo put a disclaimer on it. I just needed to calculate when a year had past.

```GO
{{- $PostYear := .Date | time.Format "2006" | int -}}
{{- $CurrentYear := now.Year | int -}}
{{- $YearDif := math.Sub $CurrentYear $PostYear -}}
{{- if ge $YearDif 1 -}}
	<p class="notice">
	  This post is over {{ if eq $YearDif 1 }} a year{{- else -}}{{- $YearDif }} years{{- end }} old. The information here may be out of date, and may not reflect my current thoughts or opinions.
	</p>
{{- end -}}
  ```
  
This was my first go at it, can you see the problem? Any post that was written in 2023, would have the disclaimer. In the span of one day, a post could be over a year old.

Unfortunately, I found this out after I pushed a build of my site with it. I'm the kind of person, when I notice an issue like that, I have to fix it. And it was already 1:30AM. Time to get to work.

After reading the Hugo docs, and a number of forum posts, and Go-lang examples. I came up with this.

```GO
{{- $PostYear := .Date -}}
{{- $CurrentYear := time.Now -}}
{{- $YearDifU := math.Sub $CurrentYear.Unix $PostYear.Unix -}}
{{- $TPostYear := .Date | time.Format "2006" | int -}}
{{- $YearDif := math.Sub (now.Year | int) $TPostYear -}}
{{- if ge $YearDifU 31536000 -}}
	<p class="notice">
	  This post is over {{ if eq $YearDif 1 }} a year{{- else -}}{{- $YearDif }} years{{- end }} old. The information here may be out of date, and may not reflect my current thoughts or opinions.
	</p>
{{- end -}}
```

This takes the time and date that a post was published on, and converts it to Unix time. It then checks to see if one year[^1] has past, compared to the current time[^2]. There's also some Hugo to print "a year" vs "[number] years" to make it read better. All that, just to get this to print, when it should.

<figure>
	<p class="notice">
	  This post is over 600 years old. The information here may be out of date, and may not reflect my current thoughts or opinions.
	</p>
	<figcaption>An example disclaimer</figcaption>
</figure>

I don't like working with time. If you want to use this, here's a [Gist](https://gist.github.com/nathnp/00cefda8e28f4d28ac929c6e930460da).

[^1]: 31536000 in Unix time 

[^2]: Time of site build, this is a static site at the end of the day.
