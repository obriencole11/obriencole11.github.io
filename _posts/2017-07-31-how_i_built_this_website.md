---
layout: post
title: How I Built This Website
tags:
- blog
- programming
date: 2017-07-31 00:00
---

![](/blog/assets/thiswebsite/mysetup.PNG)

This site is built using [Jekyll](http://jekyllrb.com/) and hosted through [Github Pages](https://pages.github.com/). The design is based on the [Hyde](http://hyde.getpoole.com/) theme and modified to suit a portfolio-structure.

**This solution costs me $0 but has cost me far more in time.**

The following is a cautionary tale, but I hope it will be helpful for those who wish to follow in my footsteps. For those looking for technical details, there's an in-depth summary at the end. For now I think it would be best to start with... 

## The story of my portfolio site adventure

<!--more-->

My first foray into programming was with web development. In my graphic design days I had even considered it as a possible career path. But when I was eventually confronted with the choice: a career in graphic design or a career in animation, I went with animation.

Fast forward a year or two, I'm pursuing animation and I need a portfolio site. Having the skills and know-how to build a basic website I thought *Why not build one myself?* Well those of you that have tried will know the answer:

## Websites are a lot of work

Today if you want to build your own site from scratch, you’re gonna hit a series of barriers. The first and I’d say the lowest barrier, is HTML and CSS. Compared to real programming languages, they’re relatively simple to learn, but do take time to fully understand. 

Then there's the design barrier. Turns out it's really easy to make a poorly designed site. One of the first traps newcomers fall into is attempting to make their site truly unique, with animated UI and fancy effects. While skilled web developers can pull it off, this typically amounts to a terrible user experience and is the reason so many sites look so similar.

The biggest barrier I’ve found however, is responsive design. Designing a web page that works on one device is relatively simple. Designing for every device however, introduces a multitude of design problems. 

Now of course all these problems can be solved by taking the time to learn. However, when web design isn’t your profession, it's tough to devote that much time to it, especially when you only need one site. 

So really in practice one of my first decisions was that I need to take...

## Shortcuts

Once I admitted I was not *actually* building my site from scratch, it was more of a decision of how much scratch was going to make up the site.

So at first my shortcuts were mostly in scope. I said *It’ll be just limited to one page* and basically built a landing page that consisted of a bunch of fancy links to other websites. It didn’t really need to exist though, at that point I could’ve just made a [Behance](https://www.behance.net/) and it’d have a better user experience.

Then I decided to just use a website template. And for some that may be a solution. I found some pretty nice theme sites that basically just give you free code to tear apart. One of the better sites I found was [HTML5 Up](https://html5up.net/), it’s basically a bunch of open source, fully-responsive, website themes. The problem was however, once I started using them I quickly hit a complexity wall. While I had full control of the code, the back end work flow was miserable. If you wanted to add a new portfolio piece you’d have to dive back into the HTML and copy and paste a bunch of code. I made one version, and when it came time to update it I ended up just throwing it out and seeking out a better solution.

At this point I began to enter the wild world of the back-end CMS (Content Management System). Basically web site generators you run on the command line. Here, design and data are kept separate, so your site is a bit easier to setup. I started with [Harp](http://harpjs.com/) since they had ported versions of [HTML5 Up templates](http://harpjs.com/blog/harp-weekly-2013-10-27). This worked well for a bit but at this point I hit another complexity barrier. Harp was in a way its own language to learn, and strapped for time I ended up doing what I set out to avoid, and resorted to using a online website builder to finally finish the site.

While I was still reluctant to sell my design freedom to squarespace or wix, I ended up deciding [WebFlow](https://webflow.com/) was my best option for control to speed ratio. For those not familiar it's similar to an online [Dreamweaver](http://www.adobe.com/products/dreamweaver.html) in terms of control.

But at this point I still wasn’t happy with it. Besides not being a site I could call my own, it was expensive. Webflow is like $20 a month and post-grad me was not financially stable enough to pay that forever. So before I set out to build *yet another* portfolio site, I needed to ask myself...

## Why Build Your Own Website?

Sure I should have questioned this from the get go, but I never really did. I like to think I was driven by the thrill of the challenge but to be honest, it was mostly my own foolish pride. So this time I needed to establish concrete reasons I should invest more time into this endeavor. In the end I established three pillars to support this choice, and I stand by them today:

#### Cost
The most influential reason I decided to build my own site again was price. If I was gonna spend the time, I better be saving money doing it.

#### Flexibility

For a while my portfolio has been a mix of strange mediums. On the same portfolio there'd be video, image, and text based media. There are plenty of templates out there that support one really well, but very few that were flexible enough to support all equally. So whatever choice I made, I decided I would need enough control in order to adapt it to fit my portfolio.

#### Fun

I’d be lying if I said this wasn’t a contributing factor. But to be honest I would have never have went down this road if I didn’t find web development fun. Web design is like a playground of visual and programming problems, it's part of the reason I ended up in technical art. And it is pretty satisfying at the end of the day to have something you made that works. Developing your own site is gonna be work, no matter what shortcut you take, might as well enjoy yourself along the way.

## My Setup

As I mentioned at the start, this site is hosted for free using [Github Pages](https://pages.github.com/). For those not familiar with the [Github](https://github.com/), it’s basically a code hosting network. However, if you store website code, Github can host it as a working website. Its truly a wonderful service, and immediately solves my cost concern. 

It does come with a few restrictions:
* The code will be public. For a portfolio site this isn’t an issue though, everything on it is public anyway!
* You need access to all the website code. This should be a no brainer though.
* It only supports static sites. This means no fancy dynamic setups with Ruby or PHP. So you can’t host a [Wordpress](https://wordpress.com/) site there. Again this was a non issue, the site was gonna be static anyway.

On the backend, the site is using [Jekyll](http://jekyllrb.com/), which Github pages has specific support for. Like Harp from earlier, its a static website generator. Basically your site is separated into HTML chunks and is built on demand. All your data entries are done in markdown files, which are basically text files with some simple formatting options.

Again, this time I had to admit I couldn’t design the site from scratch, it would just be too much time spent to reinvent the wheel. I ended up using the [Hyde](http://hyde.getpoole.com/) theme by the great [Mark Otto](https://github.com/mdo). Its built on [Poole](http://getpoole.com/) which is basically a foundation for Jekyll themes. I discovered the theme through [Fredrick Averpil’s Blog](https://fredrikaverpil.github.io/) in which I based many of my design decisions off of.

## Resources

Now I don't wish to include a complete tutorial for setting up a Jekyll site, but I think it would be inadequate to not include resources for those who do wish to use this method.

#### HTML and CSS

No matter what you're gonna need to know these two. As I said, they're not terribly difficult, especially if you already know how to program. Javascript is a bit more tricky, but honestly since learning it, I’ve rarely had to use it. So many of the problems you’d use Javascript for are fairly common, and there is no shortage of free scripts you can use to avoid writing with it entirely.

For learning all three though, I highly recommend [Codecademy](https://www.codecademy.com). Its free and offers a hands on way to learn the languages. I found it to be far easier to learn with as opposed to with a video or text tutorial.

Once you're past the basics, I'd also grab a good text editor and start experimenting on your own. [Sublime Text](https://www.sublimetext.com/) is a pretty solid editor and the free trial doesn't run out.

#### Git and Github

If you program and you don't use source control, you probably should be using source control.

Source Control or Version Control is a way of organizing versions of a code base. Unfortunately its also one of those things that are a little tough to understand why you would need it, until you need it. In short its a system that stores versions of your work. You can roll back to old versions, or "undo" parts. You can create alternate "branches" to keep different features separate, or your release code separate from your development code.

There are several different source control systems, but [Git](https://git-scm.com/) is by far the most popular and is free. Also its what [Github](https://github.com/) is built off of!

Git has the most flexibility on the command line, and there's a [pretty solid tutorial](https://www.codecademy.com/learn/learn-git) on [Codecademy](https://www.codecademy.com) if you wish to go down that path. Otherwise Github has a [free desktop application](https://desktop.github.com/) as a more visual alternative. I recommend picking up the desktop version either way, I find it easier for general use, while using the command line for debugging.

#### Jekyll and Github Pages

[Jekyll](https://jekyllrb.com/) and [Github Pages](https://pages.github.com/) are a blessing, and are the foundation of why the method works. It felt silly in the past to pay for hosting, when my website was just a couple simple pages. Jekyll may be a little tricky to set up at first, but it beats paying a monthly subscription.

Jekyll runs off of [Ruby](https://www.ruby-lang.org/en/downloads/), which you will need installed first to get anywhere. If you're on Mac or Linux, you're in luck as Ruby comes pre-installed. You can install Jekyll simply by typing `gem install jekyll` into Terminal. If you're on Windows, you have a bit more work to do. Luckily, Julian Thilo has a great guide on [How to Run Jekyll on Windows](http://jekyll-windows.juthilo.com/).

To get an actual website up, there's a [Quick Start Guide](http://jekyllrb.com/docs/quickstart/) on Jekyll's main site, but it might be overwhelming if you're starting from scratch. I recommend starting from a theme, it'll give you a better understanding on how the system works. For [Poole](http://getpoole.com/), Mark Otto has a pretty simple [setup guide](https://github.com/poole/poole#usage) that might not be a bad place to start. Otherwise there are plenty of [free Jekyll themes](http://jekyllthemes.org/) out there, although I haven't investigated those in depth.

Setting your site up with Github Pages is far easier. There's a pretty accessible guide on their [main page](https://jekyllrb.com/docs/quickstart/). Its starts you with a .github.io domain name, but I recommend buying your own. Domain names are cheap, and theres a lot of different sites you can buy from. I've used [Name Cheap](https://www.namecheap.com/) in the past, but have also heard good things about [Google Domains](https://domains.google/#/). Once you have a name, Github has a [ quick-start guide](https://help.github.com/articles/quick-start-setting-up-a-custom-domain/) on setting up the custom domain.

For site management I've also investigated some online content authoring tools. Notably [Prose.io](http://prose.io/#about) and [Forestry.io](https://forestry.io/) looked promising, but I didn't think the effort was worth it. Might be worth investigating if posting via a text editor is not for you.

#### Web Design

Design is an art form and the by far hardest of these to teach yourself. Personally, I took classes on graphic design in college, so I don't know of many free resources to offer on that end. I do think its an incredibly useful skill to learn, and if you get a chance to learn it formally, I'd take it.

In general though, I recommend if you're unsure on something, try what others are doing. It may make your site look a bit more generic, but usually the general practices are also the safest bets. For portfolio sites especially, good user experience is generally more important than interesting design. I recommend using a template for that reason.

For fonts I recommend using [Google Fonts](https://fonts.google.com/). They're free and you don't have to worry about any licenses. There's also a good amount of design resources available for them. I often will use a font pairing website like [this](http://fontpair.co/) to pick out possible combinations. For icons, [Font Awesome](http://fontawesome.io/) is wonderful. Basically every icon you want, including social media icons, in one font.

## Conclusion

Would I recommend this method to others? Honestly probably not. I think the vast majority of folks out there just want a site up, and for that Wix or Squarespace is fine. Would I recommend it as a money saving technique? Sure if you can invest the time. 

It was a several year process for me to get to where I am, and the process is still not perfect. But while the control and the free-ness is nice, at my core I was always in it for the adventure. 

And for that reason I don't regret a second of it.