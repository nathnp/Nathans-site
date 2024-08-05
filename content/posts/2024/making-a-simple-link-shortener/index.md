+++
title = 'Making A Simple Link Shortener'
date = 2024-04-29T15:40:29-04:00
draft = false
subtitle = "That link is too long"
tags = ['Web']
+++

The idea of a link shortener has always intrigued me. You give it a big link, and in return, you get a small link. The issue is, you give it a big, hard to remember link, and it gives you a small, hard to remember link. And if you want to use your own domain, most will charge you for it. So, I looked into making my own.

<h2>Give Small Link</h2>
<hr>

Turns out, making a link shortener is pretty easy. There's an HTML element that can refresh the page with a different URL. I just needed a simple page with that element. Easy. As for fixing the hard to remember part, well, its my shortener, so I can do what I want.

As an example. If I wanted a quick link to my GitHub profile, with the slug of /gh. I just have to make a folder named gh, and toss an index.html with that element in there. Boom, done.

```HTML
<!DOCTYPE html>
<html lang="en-us" dir="ltr">
<head>
<a rel="me" href="https://fosstodon.org/@nthp"></a>
<meta http-equiv="refresh" content="0; url=http://github.com/nathnp/"/>
</head>
</html> 
```

That `a` tag is for Mastodon's link verification system.

<h2>But I Don't Want To Do All That</h2>
<hr>

Having to make a folder, and paste an index file with the right link, for every link I want, would be a massive pain. So I don't. The main part of this, is a script I wrote to do it all for me. It just asks for what I want to slug to be, and for the link.

```BASH
#!/bin/bash

echo "Link Name?"
read lname
echo "link with https://?"
read llink

git pull

cd docs
mkdir $lname

cd $lname
echo "<!DOCTYPE html>" >> index.html
echo "<html lang="en-us" dir="ltr">" >> index.html
echo "<head>" >> index.html
echo "<a rel="me" href="https://fosstodon.org/@nthp"></a>" >> index.html
printf '<meta http-equiv="refresh" content="0; url='$llink'"/>' >> index.html
echo "</head>" >> index.html
echo "</html>" >> index.html

cd ../..

printf "\n\n$lname > [$llink]($llink)" >> README.md

git add docs README.md > /dev/null
git commit -m "Added $lname" > /dev/null
git push > /dev/null

echo ""
echo "link will be live at https://link.nthp.me/$lname in about one minute"
```

It will even update the readme file with the new link.

I also made a script that will generate a random slug. It just takes the first five characters of an md5 hash of the date and time. This script just asks for a description of the link[^1], and the link.

All of this is hosted using GitHub pages, and if you want to test a link, you can give this one a shot [link.nthp.me/o/3c86d](https://link.nthp.me/o/3c86d).

I'll probably make a public repo down the line with instructions on how to set this all up. But feel free to use what I've posted here, just with your own domain.

[^1]: For the readme file.