---
title: "Poem Bot: Slur Detection"
layout: post
date: 2018-07-22 01:44
headerImage: false
tag: 
- Twitter
- Python
- bot
category: blog
author: cristynhoward
description: "Screening for slurs in poems tweeted by @p0em_bot."
externalLink: false
---

The reason I initially restricted my bot to tweeting in English is because I was relying on a custom-written list of words to screen poems for slurs. Being an English-speaker, I could only generate a list of English terms to check for, and so I could only confidently allow my bot to tweet slur-free English poems.

#### Why do I need to screen poems for slurs?

Poems produced from the poemist API are written by diverse poets whose lives span a centuries. Sometimes those poems contain archiac and hurtful references to social and racial groups. For example, early on in my bot development process, my bot tweeted out a poem that contained the phrase "...righteous spilling of [racial slur] blood...". Seeing my code share something like that made me deeply uncomfortable, and I deleted it immediately. Thankfully my bot had no followers at the time. 

Now, I'm happy to let my code tweet poems that I don't understand and don't agree with. Different viewpoints and ideologies caputured in poems shared by the bot are part of what make it interesting.

However, treating my audience with respect is important to me. Followers of my bot sign up to occasionally see poems in their feed. They don't sign up to see their communities called racial slurs by a bot tweeting poems written by dead, racist, 19th-century poets. I am directly responsible if I allow my code to tweet poems that demean people on the basis of their identity, so setting up slur-detection was a must-have.

Thankfully, someone brought to my attention the github repo entitled the ["List of Dirty, Naughty, Obscene, and Otherwise Bad Words"][4]. This resource is not perfect for my use case, because I don't mind if poems include swear terms, and I doubt this list contains all common slurs in the supported languages. However, using this resource to check poems for slurs goes a long way towards preventing damaging poems from making it onto the bots Twitter page, and it allows me to enable my bot to tweet in multiple languages. 

To see the code that I wrote to detect slurs, check out the "no_bad_words" method in [helpers.py][5]. I've enabled multi-lingual slur detection, and now my bot tweets in a range of supported languages!

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">My progeny are doing things I don’t understand. <br><br>Is this what being a parent is like? <a href="https://t.co/bMBA9S1jYh">https://t.co/bMBA9S1jYh</a></p>&mdash; ⃝〇˳°. (@cristyn_howard) <a href="https://twitter.com/cristyn_howard/status/1020830798130409472?ref_src=twsrc%5Etfw">July 22, 2018</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 

[4]: https://github.com/LDNOOBW/List-of-Dirty-Naughty-Obscene-and-Otherwise-Bad-Words
[5]: https://github.com/cristynhoward/poembot/blob/master/helpers.py