+++
title = 'Being Lazy With Shortcuts'
date = 2023-11-12T17:51:01-05:00
draft = false
+++

<mark>Nov 12, 2023</mark>

At the bottom of every post. I have a reply via email button. This button does three main things. 1. It opens your default email client, 2. It pre fills the To field for you, and 3. It pre fills the subject.

This is the HTML for the reply button in this post

```HTML
<center>

<a class="button" href="mailto:reply.13a8f@nthp.me?subject=RE%3A%20Being%20Lazy%20With%20Shortcuts"> Reply to this post via email 📫</a>

</center>
```

It's pretty simple, but if you look, there are a couple of things that make it a slight pain. If you look at the `?subject=` part, you'll notice a lot of `%20`s. This is because you can't have a space in a url. The other thing you might notice. Is that there's an emoji at the end. What's so painful about that? If you look at my other posts, they each have a different emoji, on the reply button. This combination, makes it pain to add. So I wrote a shortcut.

The shortcut is pretty simple. It asks for the subject, and replaces the spaces, with `%20`s. It then will randomly select a mail themed emoji from an internal list. Finally, it copies the output to my clipboard. Then all I have to do, is paste it into Nova.

If you’d like to use this shortcut, you can click this button to add it. 

<center>
	
<a class="button" href="https://www.icloud.com/shortcuts/bcfb8006db024bbcab2b006797a8b033"> Add Shortcut </a>

</center>

<center>

<a class="button" href="mailto:reply.13a8f@nthp.me?subject=RE%3A%20Being%20Lazy%20With%20Shortcuts"> Reply to this post via email 📪</a>

For Webmail Users <br>
Address: <code>reply.13a8f@nthp.me</code><br>
Subject: <code>RE: Being Lazy With Shortcuts</code>

</center>