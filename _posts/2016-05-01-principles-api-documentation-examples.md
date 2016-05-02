---
layout: post
title: "9 Principles of Successful API Documentation In Snippet and Screenshot"
date: 2016-05-1-16 14:04:27
categories: APIs
excerpt_separator: <!--more-->
---

The third module of the Turing program focuses heavily on consuming and creating APIs, and the first thing that these masses of junior developers encounter with any API is its documentation. How to authenticate. What format requests are made in. What information to expect in a response. An API inherently exists to facilitate sharing a great resource and thus its documentation is its gateway: it either convinces developers to turn elsewhere or welcomes them in for a successful encounter. Parse Server writes that the documentation is the ["most important piece of UX for a developer"](http://blog.parse.com/learn/engineering/designing-great-api-docs/).

<!--more-->

Fortunately, there's been written a lot of good documentation on writing good documentation. Brad Fults wrote a [comprehensive list of best practices](https://bradfults.com/the-best-api-documentation-b9e46400379a#.1jefriryn). The master repository of all APIs available on the web, Programmable Web, also offers its own [list of tips](http://www.programmableweb.com/news/web-api-documentation-best-practices/2010/08/12).

Using Fults' principles, I hunted down the best representations of each idea. What follows are both examples to learn from, as well as a curated list for other developers looking for a successful place to start consuming.

## 1. Provide a good overview
Fults points out that APIs have multiple audiences: beginners, experts, and decision-makers. Thus, an API should have a good overview that addresses each of those groups.

The [Digital Public Library API Codex](http://dp.la/info/developers/codex/) does just that.
The first paragraph of their API homepage presents different jumping off points, from someone who has never used an API and will need the fundamentals, to someone ready to "dive right into the requests." It also addresses someone who might be making decisions by providing their policies and philosophy and also calls out a section for troubleshooting and a glossary.

A good overview might also link to an explanation of your ontology, taxonomy, or naming conventions for more complex APIs that rely on a lot of nested industry-specific information. DPLA does this on another page.

## 2. Document each and every call to your API separately
The [Slack API](https://api.slack.com/methods
) is enormous. Yet each call that can be made is referenced and linked to an even more detailed breakdowns.

As an example, the [Slack Methods page](https://api.slack.com/methods) lists several methods for channels.

![Slack API channel methods](/assets/apis/slack_channels.png)

Clicking one of those methods brings up a new page with more explicit detail.

![Slack archive channel](/assets/apis/slack_channels_archive.png)

While this pattern of broad overview funneling to explicit detail generates a lot of content when you have a lot of requests, it's necessary for good documentation, and leads to the next principle...

## 3. Provide all of the documentation in a single page
[Audiosear.ch's API](https://www.audiosear.ch/developer/) provides a recommendation engine for podcast series. Their method of implementing full-page documentation involves being able to show and collapse sections on each of their endpoints, as so:

![Audiosear.ch collapse function](/assets/apis/audiosearch_collapse.png)

While the documentation itself is actually pretty good, providing well-formatted information about all the parameters and response details, the page loads automatically collapsed. Developers searching out the documentation for debugging purposes would not be able to use the browser's find on page to locate the term "show_title", in this example, without expanding all the categories and manually searching first.

(Note: I later discovered the same styled format on another API, so this format seems to be the implementation of a library, but still, could be considered a flaw in the library.)

That it's a small API makes this less of a problem, but the larger the API, the more important to have at least one page where a developer can find everything at-a-glance, even if content is then linked elsewhere.

## 4. Provide complete details about both the request and the response
[Birdsong website Xeno-canto](http://www.xeno-canto.org/article/153) has a mission of "sharing bird sounds from around the world", which makes having an API a pretty obvious solution. After detailing a request and a response structure, their documentation also breaks down all the fields, a sample shown below. The more nuanced and technical your response, the more important to detail what a field might mean in the context of your API.

> * id: the catalogue number of the recording on xeno-canto
* gen: the generic name of the species
* sp: the specific name of the species
* ssp: the subspecies name
* en: the English name of the species
* ...

## 5. Use plain English in the beginning...
This hearkens back to the principle that you're creating documentation for multiple audiences. Clear, nontechnical languages helps everyone find their resources appropriately, especially those who haven't used your docs before.

Our class this year did our final exam using the [Best Buy API](http://bestbuyapis.github.io/api-documentation/?shell#overview). While I'm not a fan of its split-column table-like docs, it does have an Overview section that's easy to find and clearly explains the structure, progressively getting more specific in detail as it moves from Response Format to Errors and Postman. Anyone working with their endpoints would benefit first from reading the Overview section before heading elsewhere.

![Best Buy Overview](/assets/apis/best_buy_overview.png)

## 6. ...But provide cues and organization for the expert who is debugging
The [Spotify doc](https://developer.spotify.com/web-api/endpoint-reference/
) use navigational cues like a table of contents, links, and organized headers to provide hints to experts who are debugging. A navigational column provides keywords for using find-in-page and the top of each section has a search bar. Each element in each endpoint reference further links to an appropriate resource.

And there's nuance. In the example below, the "endpoint" and "usage" urls lead to a section detailing the request and response, while the "returns" links to a page detailing the complete object model for that resource.

![Spotify organizational cues](/assets/apis/spotify.png)

## 7. Provide a sample API key for demonstration purposes
[23 and Me's API documentation](https://api.23andme.com/docs/reference/
) is not the most cookie cutter for this idea, but still demonstrates a couple of interesting ideas. It was my API baby for the last several weeks and consequently I learned its documentation pretty well. It's an interesting API to work with: few people might have a 23 and Me account to map their genome as much as they might have a, say, Spotify account. Only being able to rely on actual users for sample data might prove tricky.

However, it does provide a demo version of all of its endpoints which returns hypothetical genetic data. The tricky part is that even this demo version still requires an access token (not to be confused with a developer's client token), but even developer accounts have that token. Some developers don't realize they still have this token to access demo data and thus the documentation could be more clear on this account. Some developers would prefer a demo access token be provided in the documentation for purposes of trying endpoints before they have an authentication method set up.

What decision an API makes about how to provide demo access to data leads into the next point...

## 8. Make it simple to copy by providing sample code
Slack responds similarly in the way it offers test access to API responses. While you need to have the correct privileges on a Slack account to try out their API within the webpage, they provide a tester feature for all of their endpoints. In this fashion, any question about an argument becomes clear by the ability to receive real data right next to the documentation on that method.

![Slack /test path](/assets/apis/slack_demo.png)

Not all APIs want to or can provide this level of functionality, but the simple solution is to provide `curl` snippets for every request.

## 9. Provide context and examples for the languages you expect to see using your API

Usually all a developer might need is curl examples. But more complex APIs with authentication schemes often (should) have sample implementations in the languages they expect to see used with their product. These are often hosted in Github repos, as [23 and Me does](https://github.com/23andMe/), or as a separate tutorials/quickstart section, as with [Google Analytics](https://developers.google.com/analytics/devguides/config/mgmt/v3/), which offers the fundamentals in Java, PHP, Javascript, and Python.

## Look, Ma, it's my first API

To further work with documentation, I'll be writing my own documentation for an API I created on my last project. Looking for more about API documentation? Make sure to read [The Best API Documentation]((https://bradfults.com/the-best-api-documentation-b9e46400379a#.1jefriryn). Wanting another resource to test APIs interactively? [Mashape](https://market.mashape.com/explore) offers a nice collection and lets you test an endpoint as well as offers snippets for each API as a curl request or one of 7 different languages. Whether you're serving or consuming, remember, good technical docs are indispensable.
