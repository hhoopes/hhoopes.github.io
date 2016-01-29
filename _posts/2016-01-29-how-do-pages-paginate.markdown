---
layout: post
title: "Learning about ERB...and actually using ERB"
date: "2016-01-29 11:50:46"
excerpt_separator: <!--more-->
---
I ran into an issue trying to get Jekyll variables for previous and next pages to work, and assumed there was some Jekyll magic I was missing. Though I was misunderstanding part of the way Jekyll variables can be chained together, what I was really missing was realizing I could apply knowledge I already had to make Jekyll better.
<!--more-->
Jekyll has variables that hold the URL for the previous page relative to the file you're in, or `page.previous.url`. However, I wanted to evaluate if there was actually a previous post, or if I was at the final one, chronologically speaking.

What I failed to realize was that I already had learned the tools necessary to allow Jekyll to evaluate that, in the form of the <B>E</B>mbedded <B>R</B>u<B>b</B>y that is already all throughout a Jekyll layout. So to add one more tiny piece of code, not <code>{% raw %}{{page.previous.url}}{% endraw %}</code>, but <code>{% raw %}{% if page.previous.url %}{% endraw %}</code>  .

I am finding I still have a disconnect as I'm thrown into learning things as quickly as possible. There's feeling like a beginner, but also testing the boundaries of what I know or could do. I still Google all the time and hope for code snippets. But sometimes I don't know that I already know how to figure out what I want to know.

In other words, in a somewhat cheesy koan, the magic isn't in Jekyll, it's in me. ;)

![meerkats!](/assets/meerkats3d-02_51265_600x450.jpg)

*Picture included because I'm still testing formatting tweaks. Enjoy the meerkat.*
