---
layout: post
title: "Dynamic technical demos, or how I tried to show that not all hackers need wear hoodies"
date: 2016-03-10 08:24:00
categories: technical communication
excerpt_separator: <!--more-->
---

As one of the requirements of Turing is that on three occasions you present a lightning talk on a technical topic, I had put a lot of thought into potential topics. I knew I wanted to try something that was more of a demonstration in nature rather than just informative. After creating and presenting a demo of cross-site scripting that was successful for several of my own criteria, including audience interaction, I offer the lessons I learned on implementing your own technical demonstration.
<!--more-->

Early on I had jokingly tweeted about wanting to use stock photography in a technical talk, since the general expectation in the infosec community is the ridiculous public perception of hackers, or at least or at least as portrayed by the media. A topic for another blog post would be how the image-driven format in technology-focused media outlets works well for gadget reporting, but lends to stereotypical presentations for more abstract science or IT topics.  

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">My first Turing lightning talk will lead w/ numerous bad stock photos of infosec, in quick succession. Maybe set to 80s movie montage music.</p>&mdash; Heidi Hoopes (@HeidiHoopes) <a href="https://twitter.com/HeidiHoopes/status/688191702562045953">January 16, 2016</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

<h3>Lesson 1: Use appropriate tools</h3>
While our module is currently focused around learning Rails to serve web apps, we started with Sinatra, a lighter weight framework than Rails with fewer "helpers" to get things done. So why did I choose to demonstrate XSS attacks on a website I built with Sinatra?  

<p>Simple. I had done research and learned that Rails already contains a lot of helper methods to validate, sanitize, and encode data. Because one of the larger points I was hoping my demonstration would drive home was that hacking code can lead to learning, I wanted a simpler tool, not something with built-in methods that might lead to a developer feeling "safe" or "complacent" about needing to understand the root problem.

While these solutions proved simple, more complex demos will ultimately require numerous demos of the demo, so to speak. Don't let your lack of tool preparation distract or break your demo when it's almost always going to be the simplest piece to address.

<h3>Lesson 2: Control the interaction</h3>
I hoped that the audience would load up the URL I offered for my demo web app, but wasn't quite sure if they would engaged. I planned as if they would and created a script to quickly drop and reset my database should my classmates choose to try out their own XSS attacks on my server.


<p>Indeed, by the second time I flipped back to the website from my slides, I was greeted by numerous pop-up alerts that had been embedded in my database. Amusingly I had lost my terminal screen in my maze of Mac mirrored screens and was only able to reset the database once, so pressed on with multiple alerts.

<p>While in some ways this effect was entirely within the expectations for the talk, it did add a little to my inner chaos. Perhaps, also, I might argue that I should've dropped the database when I wasn't interacting directly with the website, potentially to keep my audience from getting too distracted.

<h3>Lesson 3: Balance demonstration with instruction</h3>
The flow of my presentation had three examples: a simple XSS mistake or accident, another demonstrating what a real attack might look like and be countered by, and then finally an attack from a plant in the audience that used more sophisticated misuse of HTML tags.

This correspondingly let me engage the audience in a demonstration, but then provide context and instruction. The first example introduced the idea of XSS, that database rows can contain any data the user submits, even that with unintended effects when propagated to the view The second example allowed me to lead into introducing (OWASP)[http://www.owasp.org] as a resource and explaining potential attacks and defenses.</p>

<p>Finally, the last example let me pivot on my primary point that hacking teaches us about code. It let me prove in real-time that coding with an assumption of trust about a user blinds us, in this case, to how a simple image tag can be misused, rendering our intentions and perceptions meaningless.

<h3>Final score:</h3>
I got a lot of laughs for my final XSS demo(I embedded the school favorite Kazoo Kid remix in the page), and a lot of pleased feedback. If there's something you can teach even better by using a demo the audience can engage with, I suggest you take that extra time to drive the point home even better.

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">Using stock photography of hackers in a lightning talk, off the bucket list <a href="https://t.co/kbwCo2DJDM">pic.twitter.com/kbwCo2DJDM</a></p>&mdash; Heidi Hoopes (@HeidiHoopes) <a href="https://twitter.com/HeidiHoopes/status/703762680864092160">February 28, 2016</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>
