+++
title = 'Adding Tags'
date = 2023-12-02T21:51:37-05:00
draft = false
tags = ['Web', 'Hugo']
+++

After a bit of work, a fair bit of reading, and only a few failed builds. I now have post tags working on my site. This was a lot easier than I thought. So let's go over it.

There are four main things for adding tags in Hugo. Front matter, terms.html, taxonomy.html, and tag.html.

First, you have to add tags to your posts. Bellow is the front matter from my post Flight Update 3.

`Flight-Update-3.md`<br>
```MarkDown
+++
title = 'Flight Update 3'
date = 2023-08-21T23:33:55-05:00
draft = false
tags = ['Air Craziness', 'Denver 2023', 'Vacations']
+++
```

All this does, is tell Hugo what tags a post has. It won't display them for the reader. This is were `terms.html` comes in. Terms, basically puts stuff at the bottom of your posts (/pages if you want), for you. 

`terms.html`
```HTML
{{- $page := .page }}
{{- $taxonomy := .taxonomy }}

{{- with $page.GetTerms $taxonomy }}
  {{- $label := (index . 0).Parent.LinkTitle }}
  <div>
	<center>
	<div><h3>{{ $label }}:</h3></div>
	  {{- range . }}
		<a class='button' href="{{ .RelPermalink }}">{{ .LinkTitle }}</a>
	  {{- end }}
	</center>
  </div>
{{- end }}
```
<br>
This is my terms file, that I've modified a bit. By default, Hugo will generate a bulleted list of links for a posts tags. This looks... Bad. So, I changed the links to buttons, made the tags label a little bigger, and centered the whole thing. Much better.

---

Now, we need a page to display all of our tags. Hugo, again, has a default for this. It just doesn't look good. By default, Hugo will use list.html to make the tags page. Most people would probably want their tags page, to look different from their posts page. This is where taxonomy.html comes in.

Taxonomy.html is basically, your tags page. 

`taxonomy.html`
```HTML
{{ define "main" }}
  <h1>{{ .Title }}</h1>
  {{ .Content }}
  {{ range .Pages }}
	<h2><a href="{{ .RelPermalink }}">{{ .LinkTitle }}</a></h2>
  {{ end }}
{{ end }}
```

<br>
This is my taxonomy file. Its pretty much the same as list.html, just without the date printing stuff. So, it just makes a simple list of tags as links. Those links, will take you to a page of everything with that tag. Now we just need a page to show all posts, with a specific tag.

`tag.html`
```HTML
{{ define "main" }}
  <h1>Tag: <code>{{ .Title }}</code></h1>
  <p>RSS link for <code>{{ .Title}}</code> Tag --> <a href="{{ .Permalink }}feed.xml">RSS</a></p>
  {{ .Content }}
  {{ range .Pages }}
	<h2><a href="{{ .RelPermalink }}">{{ .LinkTitle }}</a></h2>
  {{ end }}
{{ end }}
```

The main interesting line here is line three. I have Hugo configured to generate an RSS feed for each tag. This line will generate a link to that feed. `{{ .Permalink }}` will print out the link for the page it is on. As an example, when generating the page for the web tag, `{{ .Permalink }}` will spit out `https://nthp.me/tags/web/`. Tacking `feed.xml` on the end of it, will add `feed.xml` to the output. `https://nthp.me/tags/web/feed.xml`. Boom, feed links.

In short, adding tag to my Hugo site was way easier than I though it was going to be. And I was even able to set up fancy things, like per tag RSS feed links.