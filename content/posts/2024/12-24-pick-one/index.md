+++
title = '12/24h Pick One'
date = 2024-05-27T14:07:00-04:00
draft = false
subtitle = "2PM comes after 1900"
tags = ['Rant']
+++

I can't talk about my work. There's too much red tape, but I can complain about something stupid in one of our main software tools.

<p class="notice"><b>Note</b>: If you work at my work, this post does not contain any internal information (tool names, capabilities, or purposes).</p>

<h2>Time</h2>
<hr>

We have a number of software tools where I work. One of them we use everyday. One of the fields in that software, let's us input a time. With how much we use that field, you'd think it would work well, right?

All of our paper work is in 24h time. That field in our main tool, is 12h. But, it accepts 24h input... kinda.

If I type in something like 15 into the hour field, that gets resolved to 3PM. Cool. However, if I input something like 20, I never get to input the zero, right after I hit 2, it moves to the minute field... and it doesn't update the AM/PM field.

Here's a quick table of the behavior.

| Input | Result         |
|-------|----------------|
| 05    | 05:MM:SS AM/PM |
| 13    | 01:MM:SS PM    |
| 19    | 07:MM:SS PM    |
| 21    | 02:1M:SS AM/PM |

There isn't a setting to change this, and as far as I know, it "isn't" a bug. Its been like this for years. I just need to find the right person internally to yell at.