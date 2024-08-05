+++
title = 'Writing a Post'
date = 2023-11-14T18:24:27-05:00
draft = false
subtitle = 'No pencil needed'
tags = ['Web', 'Apple Shortcuts']
+++

Posting on a static site is interesting. You don’t fire up a website and start typing. Nor do you just drag and drop photos. You have to make the whole web page, yourself. It’s not that hard. Though, it can be confusing if you’re used to a CMS. Here’s my work flow. 

## Writing

I start off by firing up [Nova](https://nova.app). In it I have three projects for this site. Dev, Pub, and Prod. Dev, is where I do all my work. Pub, is a public snapshot of Dev that gets updated when changes are pushed to Prod. Prod, is production. This is where Github serves the site from. Pushing changes to here will cause Github to automatically redeploy the site, with those changes. 

Drafts are written in Dev, so I open up that project. I start off by running the command `hugo new content posts/<filename>.md`. Why do this rather than just making a new file? Simple, running this will pre-fill the file with stuff I don’t want to type. 

```Markdown
+++
title = 'Writing a Post'
date = 2023-11-14T17:19:27-05:00
draft = true
+++

!!ADD PUB DATE!! <br>
!!SET FRONTMATTER PUB DATE!! <br>
!!SET DRAFT FLAG!!
```

There are two main things here. The first is at the top. That's the front mater for this post. It basically tells Hugo about the post. Title, publishing date, and whether or not it it’s a draft. The second thing, is a bunch of reminders. These remind me to 1. Set the publishing date on the page. 2. Set the publishing date in the front mater. And 3. Set the draft flag so it can be published. 

After the file is created, I then run `hugo server -D`. This will start a local web server with my site. That way I can see exactly how my post will look, before I push it to Prod. And then, I write. 

The post files are written in Markdown. A super easy to learn (and read) markup language. You can see an example by looking at this site’s [public repo](https://github.com/nathnp/Nathans-site) on Github. Things get a little interesting when it comes to images, and replies. 

### Adding Images

Images can be a minor pain at first, till you get the hang of it. First, you need an image. In Hugo, images go in the `static` folder. To help with organization, I also use sub folders. `static/pics/<post name>/`. Pictures will get named `fig<number>`, and gifs will get named `gif<number>`. Now I can easily call the image using Markdown in the post. 

`![](/posts/writing-a-post/fig1.webP)`[^1]<br>
`![](/posts/writing-a-post/gif1.gif)`[^2]

### Replies

Due to the nature of a static site, comments are a monster pain to do. So many don’t. Besides, who wants to moderate them anyway. So most blogs will have a reply by email button. 

This is added with some simple HTML. Though you might be thinking, that sounds like a pain to put at the end of every post. Well, we can automate its generation. I made a simple Shortcut on my Mac to do exactly that. All I have to do is run it, give it the title, and it will plop ready to paste HTML, into my clipboard. 

```HTML
<center>

<a class="button" href="mailto:reply.65tu8@nthp.me?subject=RE%3A%20Writing%20a%20Post"> Reply to this post via email 📮</a>

For Webmail Users <br>
Address: <code>reply.65tu8@nthp.me</code><br>
Subject: <code>RE: Writing a Post</code>

</center>
```

## Proofreading

Proofreading, sucks. I’ll read over a post two to three times. Correcting errors each pass through, and still find some until after posting. 

## Posting

Posting isn’t as simple as just clicking a post button. I need to turn this MD file, into a full blown HTML file. This is easy. All I have to do, is run the command `hugo`. Hugo will then spit out my site, ready to serve in the `public` folder. Then I copy then contents of public folder to Prod. Everything else in Dev will get copied over to Pub. After that, I push both up to Github. 

Prod is the only one that does something special. When Github sees a new commit in that repo. It’ll copy all the files into a container, and deploy the site from there. All automatically. Yay!

## Thoughts

So yeah. This all sounds pretty complicated when you break it down. But in practice, it’s actually pretty straightforward. And you can automate all of the repetitive stuff away. 

A blog post, about writing a blog post. Weird. 

[^1]: There’s nothing there, don’t bother looking. 

[^2]: Nothing here at all, I promise
