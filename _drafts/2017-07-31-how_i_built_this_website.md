---
layout: post
title: How I Built This Website
tags:
- blog
- programming
date: 2017-07-31 00:00
---

![](/blog/assets/thiswebsite/mysetup.png)

This site is built using [Jekyll](http://jekyllrb.com/) and hosted through [Github Pages](https://pages.github.com/). The design is based on the [Hyde](http://hyde.getpoole.com/) theme, and modified to suit a portfolio-structure.

#### This solution cost me $0 but cost me much more in time.

To prevent others from succumbing to my fate, here is...

## The story of my portfolio site adventure

<!--more-->

My first foray into programming was with web development. In my graphic design days I had even considered it as a possible career path. But when I was eventually confronted with the choice: a career in graphic design or a career in animation, I went with animation.

Fast forward a year or two, I'm pursuing animation and I need a portfolio site. Having the skills and know-how to build a basic website I thought "Why not build one myself?" Well if any of you have tried building your own site you'd know the answer...

## Websites are a lot of work

Today if you want to build your own site from scratch, you’re gonna hit a series of barriers. The first and I’d say the lowest barrier, is html and css. Compared to real programming languages, they’re relatively simple to learn. Javascript is a bit more tricky, but honestly since learning it, I’ve rarely had to use it. So many of the problems you’d use javascript for are fairly common, and there is no shortage of free scripts you can use to avoid writing it entirely.

Then there's the design barrier. Turns out it's really easy to make poorly designed sites. One of the biggest tidbits I recalled from my graphic design days is that **good design is invisible**. And it practice that's fairly difficult, and likely the reason most sites look so similar.

The biggest barrier I’ve found however, is responsive design. Designing a web page that works on one device is relatively simple, designing for every device introduces a multitude of design problems. 

Now of course all these problems can be solved by taking the time to learn. But when web design isn’t your profession, it's tough to devote that much time to it, especially when you only need one site. 

So really in practice one of the first decisions I made is that I need to...

## Take Shortcuts

At this point once I admitted I’m not *actually* building my site from scratch, it was more of a decision of how much scratch was going to make up the site.

So at first my shortcuts were mostly in scope. I said “It’ll be just limited to one page” and basically built a landing page that really just a bunch of fancy links to other websites. It didn’t really need to exist though, at that point I could’ve just made a behance and it’d have a better user experience.

Then I decided to just use a website template. And for some that may be a solution. I found some pretty nice theme sites that basically just give you free code to tear apart. One of the better sites I found was [HTML5 Up](https://html5up.net/), it’s basically a bunch of open source, fully-responsive, website themes. The problem however, once I started using them was I hit a complexity wall. While I had full control of the code, the back end workflow was miserable. If you wanted to add a new portfolio piece you’d have to dive back into the html and copy and paste a bunch of code. I made one version, and when it came time to update it I just threw it out and sought out a better solution.

At this point I began to enter the wild world of the back-end CMS (Content Management System). Basically web site generators you run on the command line. Here, design and data are kept separate, so your site is a bit easier to setup. I think I started with [harp](http://harpjs.com/) since they had ported versions of [HTML5 Up templates](http://harpjs.com/blog/harp-weekly-2013-10-27). This worked a bit but at this point I hit another complexity barrier. Harp was in a way its own language to learn, and strapped for time I ended up doing what I set out to avoid, and used a website generator.

While I was still reluctant to sell my design freedom to squarespace or wix, I ended up deciding [WebFlow](https://webflow.com/) was my best option for control to speed ratio. For those not familiar it's similar to an online [Dreamweaver](http://www.adobe.com/products/dreamweaver.html) in terms of control.

But at this point I still wasn’t happy with it. Besides not being a site I could call my own, it was expensive. Webflow is like $20 a month and postgrad Cole was not financially stable enough to pay that forever. So before I set out to build *yet another* portfolio site, I needed to ask myself...

## Why Build Your Own Website?

Sure I should’ve questioned this from the get go, but I never really did. I like to think I was driven by the thrill of the challenge but to be honest, it was mostly my own foolish pride. So this time I need to establish concrete reasons I should invest more time into this endeavor. In the end I established three pillars to support this choice, and I stand by them today:

#### Cost
The most influential reason I decided to build my own site again was cost. If I was gonna spend the time to build my own site, I better be saving money doing it.

#### Flexibility

For a while my portfolio has been a mix of strange mediums(and kinda still is in a more focused way). If I was an illustrator a website with a wall of images would be my go to. If I was purely an animator, a wall of videos would be ideal. And if I was purely a programmer a wall of text would suffice. Now there are not a ton of portfolio options that support all three of those mediums equally. So whatever choice I made, I decided I would need enough control to adapt it to my portfolio.

#### Fun

I’d be lying if I said this wasn’t a contributing factor. But to be honest I would have never have went down this road if I didn’t find web development fun. Web design is like a playground of visual and programming problems, it's part of the reason I ended up in technical art. And it is pretty satisfying at the end of the day to have something that works that you created. Developing your own site is gonna be work, no matter what shortcut you take, might as well enjoy myself all the way.

## My Solution

As I mentioned at the start, this site is hosted for free using [Github Pages](https://pages.github.com/). For those not familiar with the Github, it’s basically a code hosting network. If your code happens to be website code, Github can host it as a working website. Its truly a wonderful service, and immediately solves my cost concern. It does come with a few restrictions:
The code will be public. For a portfolio site this isn’t an issue though, everything on it is public anyway!
You need access to all the website code. This should be a no brainer though.
It only supports static sites. This means no fancy dynamic setups with Ruby or PHP. So like you can’t host a wordpress site here. Again this is a non issue, the site was gonna be static anyway.

On the backend, the site is using [Jekyll](http://jekyllrb.com/), which Github pages has specific support for. Like Harp from earlier its a static website generator. Basically your site is separated into html chunks and is built on demand. All your data entries are done in markdown files, which are basically text files with some formatting options.

Again I had to admit I couldn’t design the site from scratch, it would just be too much time spent to reinvent the wheel. I ended up using the [Hyde](http://hyde.getpoole.com/) theme by [Mark Otto](https://github.com/mdo). Its built on [Poole](http://getpoole.com/) which is basically a foundation for jekyll themes. I discovered the theme through [Fredrick Averpil’s Blog](https://fredrikaverpil.github.io/) in which I based many of my design decisions off of.

Would I recommend this method to others? Maybe. I think for the vast majority of folks out there who just need a quick site and not worry about it, a Wix or Squarespace site is fine. While the control and the free-ness is nice, at my core I'm in it for the adventure.