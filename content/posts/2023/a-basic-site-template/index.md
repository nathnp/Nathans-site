+++
title = 'A Basic Site Template'
date = 2023-12-23T20:06:34-05:00
draft = false
subtitle = "Where will it take me?"
tags = ['Web', 'Hugo']
+++

I have two jobs, one of them is as a cybersecurity TA. One of the projects we have the students do, is to deploy a basic website in an Azure container. While they're working on there site, we discuss the benefits of a personal site, and why they should have at least a basic one. The students can keep their site up if they want[^1], but Azure is pricey. So, I had an idea.

The project gives them a starting template for their site[^2]. The students are free to deviate from that template, but they start out with one. My thought was, with how much we say that they should have their own site. And with how much Azure can cost. Why not make a basic template for use outside of Azure[^3].


So I made `Basic Site Template`, it’s exactly what it sounds like. My goal was to have an easy to understand template, that doesn't look like crap when rendered. The template is only 39 lines, and has clear labels of what goes where.

<details><summary>Template index.html</summary>

```HTML
<!DOCTYPE html>
<html lang="en-us" dir="ltr">
	<head>
		<meta name="viewport" content="width=device-width">
		<link rel="stylesheet" href="https://cdn.simplecss.org/simple.min.css">
	</head>
	<title>SITE TITLE</title>
	<body>
		<header>
			<h1>SITE TITLE</h1>
			<nav>
				<ul>
					<li>
						<a href='LINK'>LINK 1</a>
					</li>
					<li>
						<a href='LINK'>LINK 2</a>
					</li>
				</ul>
			</nav>
		</header>
		<main>
			<center>
			<img src='/pics/FILENAME' width='256' height='256'/> <br>
			
			<p>ABOUT YOU</p>
			
			<p><a class='button' href='mailto:YOUR EMAIL'>Contact Me!</a></p>
			
			</center>
		</main>
		<footer>
			<p>Copyright NAME 2024
				<br>
			Site made with <a href='https://simplecss.org'>Simple.CSS</a>
			</p>
		</footer>
	</body>
</html>	
```

</details>

I’ve learned from my students, that examples go a long way. Not only did I put examples in the readme instructions, I also spun up a simple demo site. The demo site is hosted out of the demo branch, so its index file is easily viewable[^4]. 

I’m hoping this will help a few students get a basic landing page up. I even dropped a link to the GitHub pages docs for free hosting. I might follow this post up in a few semesters with how’s it’s gone.

You can find the GitHub repo [here](https://github.com/nathnp/Basic-Site-Template)

[^1]: After grading, the student has to take up the hosting costs. 

[^2]: The project is a mixture is them writing their own site, and deploying it. 

[^3]: They can rip the index file out of the container if they want, however they’d also have to rip out the CSS file.

[^4]: I put a link to it in the readme, I know how my students can be. 