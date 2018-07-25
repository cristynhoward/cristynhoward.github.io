---
title: "Harvard Art Museum Bot"
layout: post
date: 2018-07-25 01:44
headerImage: false
tag: 
- Twitter
- Python
- bot
category: project
projects: true
author: cristynhoward
description: "Learn a little bit about @art_museum_bot."
externalLink: false
---

I was browsing [Programmable Web's API Directory][1], when I came across the [Harvard Art Museum API][2]. Having just set up my [@p0em_bot][3], I immediately recognized that I could use this resource to construct another fun art bot, so I went straight to work.

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">Carp Climbing a Waterfall<br>Totoya Hokkei<br>Prints<br>Japanese, Edo period, circa early 19th century <a href="https://t.co/dlUshWAflg">pic.twitter.com/dlUshWAflg</a></p>&mdash; Art Museum Bot (@art_museum_bot) <a href="https://twitter.com/art_museum_bot/status/1021992870369222661?ref_src=twsrc%5Etfw">July 25, 2018</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 

The source code for the bot is available [here][4]. It was pretty easy to build -- I would say the hardest part was carefully selecting which fields in the object records should be used to generate the tweeted description, and then designing a method that would generate an informative description for any object regardless of blank fields.

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">This is a page from what is known as the Housley Sketchbook, containing sketches of landscapes. The sketchbook has now been dismantled and the pages dispersed.<br><br>Martin Johnson Heade<br>Drawings<br>American, 1860 <a href="https://t.co/8QLtNJBL4N">pic.twitter.com/8QLtNJBL4N</a></p>&mdash; Art Museum Bot (@art_museum_bot) <a href="https://twitter.com/art_museum_bot/status/1022000414722609153?ref_src=twsrc%5Etfw">July 25, 2018</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 

Funnily enough, in my eagerness to complete this project, I never stopped to check if it had been done before. Thankfully, it looks like no one has ever made a Twitter bot using the Harvard Art Museum API, so my code is bringing objects and artifacts to from their archives to Twitter for the first time. 

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">&#39;Guang&#39; Covered Ritual Wine Vessel with Animal, Bird, and &#39;Taotie&#39; Decor<br>Vessels<br>Chinese, early Western Zhou period, mid 11th-early 10th century BCE <a href="https://t.co/PArVlAxFys">pic.twitter.com/PArVlAxFys</a></p>&mdash; Art Museum Bot (@art_museum_bot) <a href="https://twitter.com/art_museum_bot/status/1021845024408043520?ref_src=twsrc%5Etfw">July 24, 2018</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 

However, it turns out that a lot of museums have APIs and/or open data initiatives, and lots of other developers have independently had the same idea as me! There are numerous active Twitter bots that also tweet out objects from museum archives, including [@PhilaMuseumBot][5], [@LACMAbot][6], [@WaltersArtBot][7], and [@guggenheimbot][8].

Wonderful news for my fellow art-lovers on Twitter!

[1]: https://www.programmableweb.com/category/all/apis
[2]: https://www.programmableweb.com/api/harvard-art-museums
[3]: https://cristynhoward.github.io/poem-bot/
[4]: https://github.com/cristynhoward/artmuseumbot
[5]: https://twitter.com/PhilaMuseumBot
[6]: https://twitter.com/LACMAbot
[7]: https://twitter.com/WaltersArtBot
[8]: https://twitter.com/guggenheimbot
